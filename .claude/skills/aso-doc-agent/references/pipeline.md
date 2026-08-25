---
source-git-commit: ed1960cc0364dc4169a454a4860b7463890e3b74
workflow-type: tm+mt
source-wordcount: '2275'
ht-degree: 0%

---
# Agent de document ASO — Pipeline

Référencé à partir de `SKILL.md`. Ceci est la source de vérité pour l&#39;ordre d&#39;exécution ; SKILL.md est
le résumé. Lisez `config.yml` avant de commencer : chaque valeur dans `{braces}` ci-dessous est une valeur
clé de configuration.

**Gestion des erreurs (s’applique à chaque étape ci-dessous).** Un appel d’outil/API contenant des erreurs (authentification
échec, expiration du délai, requête incorrecte, schéma inattendu) n’est jamais la même chose qu’un
résultat vide légitime, et ne doit jamais être laissé tomber en silence dans un
branche « vide » ou « rien à faire » (par exemple, l’étape 1.2 est « rien à faire ici », l’étape 3.3 est « rien à faire ici »).
« arriéré épique entièrement couvert ou tout en cours »). En cas d’erreur d’appel, arrêtez et enregistrez le
erreur réelle dans le résumé d’exécution au lieu de continuer comme si elle était correctement renvoyée.

## Étape 0 — Contrôle en amont

1. `pwd` et vérifiez `guidelines.md` + `.claude/skills/aso-doc-agent/config.yml` existent. Si ce n&#39;est pas le cas, arrêter — mauvais répertoire.
2. `gh auth status` — vérifiez que le compte `sandsinh_adobe` dispose d&#39;un jeton valide sur cet hôte. **Ne jamais exécuter`gh auth switch`** — il retourne le compte de `gh` actif à l&#39;échelle de la machine comme un effet secondaire, ce qui peut bloquer silencieusement tout autre terminal/processus sur cette machine sur le mauvais compte pour une exécution quotidienne sans surveillance. Au lieu de cela, définissez la portée de cette exécution uniquement : `export GH_TOKEN=$(gh auth token --user sandsinh_adobe)` une fois au début, de sorte que chaque appel `gh` ci-dessous utilise ce jeton via la variable d’environnement `GH_TOKEN`, quel que soit le compte globalement actif.
3. `mkdir -p {state_dir}` si manquant.
4. Lisez `{state_dir}/run-state.json` s’il existe (sinon traitez-le comme `{"runs_completed": 0, "tracked_prs": []}`). `tracked_prs` est la propre liste de `{number, headRefName, key}` de cet agent pour les relations publiques qu’il a ouvertes - utilisée uniquement pour détecter une relation publique qui s’est fermée sans fusionner (étape 1.5), car `gh pr list --state open` seul ne peut pas la voir une fois qu’elle est partie. Le minutage des demandes de média réside dans un fichier distinct, `{state_dir}/media-requests.json` (étape 5) — GitHub et Jira restent la source de vérité pour tout le reste (statut PR, statut du ticket).
5. `--ticket KEY` présent -> ignorez la sélection automatique de l’étape 3, utilisez la touche directement (exécute toujours les étapes 4 à 7). Sinon, sélectionnez automatiquement à l’étape 3.

## Etape 1 — Rapprocher les exécutions précédentes

Exécutez cette opération à chaque fois, même sur une exécution avec point d’entrée ou vide.

1. `gh pr list --repo {github.repo} --label {github.pr_label} --state open --json number,url,isDraft,headRefName,title,reviewDecision`
2. **Vérification — Chaque requête de tirage ouverte, chaque exécution** (`pr.check_reviews_every_run`) :
   - `gh pr view <number> --repo {github.repo} --json reviewDecision,reviews,comments`
   - `reviewDecision == "APPROVED"` -> fusionner maintenant : `gh pr merge <number> --repo {github.repo} --merge`. Vérifiez que la fusion a bien atterri (`gh pr view <number> --json state,mergedAt` - `state == "MERGED"`) avant de la traiter comme terminée ; un rejet de branche protégée ou une vérification requise toujours en attente peuvent laisser la requête de tirage ouverte même après l’appel de `gh pr merge`, et cela doit être consigné comme un échec, et non signalé à Jira comme fusionné (il s’agit d’une fusion normale approuvée par l’homme, et non d’une fusion basée sur le délai d’expiration). Lors de la fusion confirmée : laissez un commentaire sur le ticket Jira lié qu’il a fusionné et déposez la requête de tirage de `tracked_prs`.
   - `reviewDecision == "CHANGES_REQUESTED"` -> ne **pas** corriger automatiquement la RP dans cette version. Lisez les commentaires de révision (`gh api repos/{github.repo}/pulls/<number>/comments` pour les commentaires intégrés, ainsi que le corps de révision de niveau supérieur à partir du champ `reviews` ) et exécutez **Apprendre à partir des commentaires** ci-dessous. Consignez le PR comme étant en attente d’action de création dans le résumé d’exécution. Si ce PR a été `CHANGES_REQUESTED` depuis plus de `pr.stale_after_hours` sans mise à jour, signalez-le comme périmé pour le point d&#39;accès de l&#39;étape 2 - il reste ouvert pour un humain mais n&#39;occupe plus un emplacement de bouchon.
   - Tout le reste (pas encore d&#39;avis, `REVIEW_REQUIRED` sans avis envoyé) -> rien à faire ici.
3. **Apprenez-en davantage grâce aux commentaires.** Pour chaque commentaire ou corps de commentaire de révision qui se lit comme un *généralisable* remarque sur le ton, la structure ou le contenu, et non comme un correctif ponctuel spécifique à cette requête de tirage (comparez « toujours mentionner l’onglet Ignoré pour les opportunités avec prise en charge d’exclusion » par rapport à « faute de frappe à la ligne 12 »), ajoutez une entrée datée et liée au ticket à `references/review-learnings.md`. Ignorer les retours purement mécaniques (fautes de frappe, liens cassés, peluche) — corrigez ceux dans la RP elle-même, ils n&#39;ont pas besoin d&#39;une leçon durable. Le format d’entrée exact est documenté dans ce fichier.
4. Pour chaque requête d’extraction **brouillon** de cette liste, extrayez la clé Jira du nom de la branche (`{github.branch_prefix}<KEY>-...`).
   - `mcp__Corp-Jira__list_attachments` + `mcp__Corp-Jira__get_jira_comments` sur cette clé.
   - Recherchez : une nouvelle pièce jointe d’image correspondant à la capture demandée, OU un commentaire contenant une URL `video.tv.adobe.com`.
   - S’il est trouvé : `git fetch`/`checkout` la branche, ajoutez l’image à `help/**/assets/` (s’il s’agit d’une pièce jointe d’image, téléchargez via `download_attachment`) ou remplissez l’espace réservé `>[!VIDEO](...)` (s’il s’agit d’un commentaire d’URL vidéo), validez par rapport à `experience-league-markdown`, validez, envoyez une notification push, `gh pr ready <number>`, commentez sur la requête de publication « Media added — ready for review », mettez à jour `{state_dir}/media-requests.json` entrée vers `resolved`.
   - Si introuvable : vérifiez le temps écoulé depuis la demande en `{state_dir}/media-requests.json`. Appliquez la logique d’escalade/d’abandon à partir de l’étape 5 ici également (un brouillon de requête de tirage ouvert sur plusieurs exécutions doit toujours être poursuivi par son média), y compris l’appel de `gh pr ready` du chemin d’abandon, de sorte qu’un brouillon donné peut toujours être examiné au lieu de rester bloqué.
5. **Détecter les PR fermées sans fusionner.** Comparez la liste open-PR de cette exécution (étape 1) aux `tracked_prs` de `run-state.json`. Toute RP suivie manquante dans la liste ouverte, et non confirmée fusionnée à l’étape 2, a été fermée sans fusion — avant de la supprimer, de récupérer son état final (`gh pr view <number> --repo {github.repo} --json reviews,comments`) et d’exécuter **tirer des leçons des commentaires** une dernière fois dessus, de sorte que le raisonnement de rejet d’un humain ne soit pas perdu. Puis supprimez-le du suivi. Aucune autre action n’est nécessaire sur le ticket lui-même : puisque le libellé de réclamation n’est appliqué qu’au moment de la publication (étape 6.10), un ticket fermé, non fusionné, n’a déjà aucun libellé et les vérifications de l’étape 3.2 (pas de RP ouvert/fusionné) le rendent naturellement éligible pour être sélectionné à nouveau lors d’une exécution future.
6. Définissez `tracked_prs` dans `run-state.json` sur la liste Open-PR actuelle (`number`, `headRefName` et la clé Jira analysée à partir du nom de la branche), pour que l’étape 5 de l’exécution suivante fournisse la comparaison.

## Étape 2 — Porte du bouchon PR

1. Comptabilisez les PR ouvertes à partir de la sortie `gh pr list` de l’étape 1, à l’exclusion de toute PR marquée à l’étape 1.2 comme périmée (`CHANGES_REQUESTED` ouverte plus longtemps que `pr.stale_after_hours` sans mise à jour) — celles-ci restent ouvertes pour un humain mais n’occupent plus d’emplacement de limitation.
2. Si count >= `{pr.max_open}` (3) : `"cap reached ({count}/{pr.max_open} open) — skipping new ticket this run"` journal, passez à l’étape 7.
3. Sinon, passez à l’étape 3.

## Étape 3 — Choisir un ticket

Ignorer complètement si `--ticket KEY` a été passé (utiliser KEY).

```
JQL: "Epic Link" = {jira.epic} AND status = "{jira.open_status}"
     ORDER BY priority DESC, created ASC
```

1. Exécutez la recherche (`mcp__Corp-Jira__search_jira_issues`, `minimizeOutput: true`, champs limités à `key,summary,priority,status,labels`).
2. Promenez les résultats dans l’ordre. Ignorer les tickets qui :
   - porte déjà le libellé `{jira.picked_label}`, OU
   - dispose déjà d’une branche `{github.branch_prefix}<KEY>-*` sur le serveur distant (`git ls-remote --heads origin '{github.branch_prefix}<KEY>-*'`), OU
   - a déjà une requête de tirage ouverte ou fusionnée (contre-vérification avec la liste / `gh pr list --state all --search <KEY>` de l’étape 1).
3. Le premier billet qui réussit les trois chèques est le choix. Si aucun n’est transmis **car la recherche n’a véritablement renvoyé aucun ticket éligible**, connectez-vous `"epic backlog fully covered or all in flight"` et passez à l’étape 7. Si la recherche elle-même a échoué (erreur d’authentification, délai d’expiration, JQL incorrect), ce n’est pas le cas - consignez plutôt l’erreur réelle (voir Gestion des erreurs ci-dessus).
4. N’étiquetez **pas encore** ticket : le libellé de réclamation est appliqué à l’étape 6.10, une seule fois qu’une branche et un PR existent réellement. Les étapes 4 à 5 (recherche/brouillon/média) peuvent échouer ou se bloquer sans laisser de trace sur le ticket ; les seuls signaux en cours avant l’étape 6 sont les contrôles d’existence de branche/de pré-existence ci-dessus, ce qui est suffisant étant donné qu’ils s’exécutent à partir d’une seule machine sans réelle simultanéité à éviter.

## Étape 4 — Recherche + ébauche

La recherche vient en premier et est **multi-source** — ne jamais rédiger à partir d&#39;une seule entrée (la Jira
uniquement un ticket ou simplement la lecture de documents frères). Chaque source sous confirme ou
corrige les autres ; les contradictions sont résolues en faisant confiance au code source > Wiki/PR docs >
discussion sur Slack > inférence du rédacteur/de la rédactrice, dans cet ordre, et être marqué en ligne
comme `<!-- CONFIRM -->` lorsqu’ils ne peuvent pas être résolus.

0. **Cours de révision cumulés.** Lis d&#39;abord `references/review-learnings.md`. Appliquez tout ce qui est pertinent pour le sujet de ce ticket avant de le rédiger — c&#39;est ainsi que les commentaires des révisions de RP passées améliorent les brouillons futurs au lieu de répéter la même correction.

### Recherche (faites tout ce qui s&#39;applique — ne passez pas directement à la rédaction)

1. **Code Source (vérité de base sur son fonctionnement réel).** Recherchez dans le référentiel de l’interface utilisateur principale (`research.code_repos` dans config.yml) l’adaptateur/gestionnaire de la fonctionnalité (`*OpportunityAdapter.tsx`, `*SuggestionAdapter.tsx`), son hook de données (`use*Data.ts`) et ses chaînes de titre/description `.l10n.ts`/`.I10n.ts`. Il s’agit de l’autorité pour les noms de champ, la forme de données, la catégorie et la copie exacte du produit, préférez-la à toute autre chose lorsque les sources ne sont pas d’accord.
2. **Wiki (intention de conception, spécifications, décisions).** `mcp__Adobe-Wiki__search_wiki_content` avec le nom de la fonctionnalité/opportunité et la clé epic/ticket. Lisez les pages correspondantes (`get_wiki_content`) pour connaître la raison d’être de la fonctionnalité, la terminologie utilisée par l’équipe produit, les cas de flux d’expérience utilisateur ou de périphérie documentés et les captures d’écran intégrées qui définissent l’aspect réel de l’interface utilisateur (renseigne la spécification de capture multimédia à l’étape 5, ne remplace pas une nouvelle capture d’écran réelle, sauf si la page est à jour).
3. **Slack (comment l&#39;équipe en parle réellement, questions ouvertes, modifications récentes).** `mcp__Slack__slack_search_messages` avec le nom de la fonctionnalité/opportunité et la clé de ticket, sans restriction par canal, sauf si `research.slack_channels` la réduit dans config.yml. Recherchez : les messages d’annonce (qui bénéficient souvent d’un framing soigné destiné aux clients), les threads de discussion sur la conception et tout ce qui indique que la fonctionnalité a récemment été modifiée d’une manière similaire aux documents ou commentaires de code frères ne se refléterait pas encore.
4. **Historique des relations publiques de GitHub (justification de l’implémentation, captures d’écran, discussion de révision).** `gh search prs --repo <repo> "<feature name>"` ou `gh pr list --repo <repo> --search "<ticket key OR feature name>" --state all` à travers les `research.code_repos`. Lisez les descriptions des relations publiques fusionnées pour en connaître la logique, les documents de conception liés et les captures d’écran qui clarifient le comportement que le code seul n’explique pas (par exemple, pourquoi un type de correctif est bloqué, à quoi ressemble un scénario de périphérie dans l’interface utilisateur).
5. **Analogues de tons.** En fonction du résumé du ticket, recherchez les pages existantes 2 à 3 les plus proches :
   - « ... tickets pratiques pour opportunités » -> lisez 2 fichiers frères dans `help/documentation/opportunities/` (l’emplacement pratique réel par opportunité - `help/opportunity-types/*.md` sont les pages de destination de catégorie avec des grilles de cartes liées à celles-ci, et non le contenu pratique lui-même).
   - Paramètres/workflow/tickets de connexion -> lecture de 1 à 2 fichiers frères dans `help/documentation/` (cochez `setup/`, `opportunities/`, `settings.md`, `basics.md` pour la correspondance la plus proche).
     Structure de titre miroir, utilisation de la zone de notes, longueur de la phrase, niveau de détail technique.
6. **Règles de format.** Relisez la référence rapide de `experience-league-markdown` compétence avant d’écrire. Chaque en-tête/note/image/lien doit correspondre exactement à sa syntaxe.

### Brouillon

7. **Décision du fichier cible.** Préférez l’extension de la section appropriée d’une page existante à la création d’un nouveau fichier, SAUF SI le ticket correspond à la granularité des pages autonomes existantes (par exemple, chaque opportunité obtient son propre fichier sous `help/documentation/opportunities/` - un nouveau fichier suit la structure exacte d’un frère existant). Lors de l’extension d’une page existante, ne touchez qu’une seule section pour ce ticket — ne modifiez pas les sections non liées même si elles semblent obsolètes. Si vous créez une page autonome, ajoutez également sa carte à la page de destination `help/opportunity-types/*.md` correspondante (liste de commentaires source + bloc HTML généré, correspondant au modèle exact des cartes existantes) et enregistrez-la dans `help/main-toc/TOC.md`.
8. **Version préliminaire v1.** Écrivez le contenu maintenant (en mémoire / entièrement, pas encore dans le fichier référentiel — cela se produit à l’étape 6 après la décision du média, de sorte qu’un document en attente de média et un document résolu par le média passent par le même chemin d’écriture). Synthétisez toutes les étapes 1 à 6 - ne vous contentez pas de reformuler la description du ticket Jira.
9. **Itération.** Relisez le brouillon v1 par rapport à chaque résultat de recherche des étapes 1 à 4 : le brouillon a-t-il manqué quelque chose de Slack ou de Wiki ? Cela contredit-il ce que le code source fait réellement ? Correspond-il aussi étroitement que possible au ton de son frère ? Révisez avant de passer à autre chose — il s&#39;agit d&#39;une véritable deuxième passe, et non d&#39;une formalité. Tout ce qui n&#39;est toujours pas confirmé après cette passe (qui n&#39;est trouvé dans aucune des quatre sources) obtient un commentaire `<!-- CONFIRM -->` en ligne plutôt qu&#39;une supposition.
10. **Décision du média.** Décidez `mediaNeeded: true|false`.
    - `true` si la fonctionnalité est un workflow d’interface utilisateur à plusieurs étapes dans lequel une description textuelle seule serait matériellement plus difficile à suivre (correspond à « utilisé judicieusement... par `guidelines.md` lorsqu’une description textuelle est insuffisante »).
    - Si `true`, produisez : `mediaType` (`screenshot` ou `video`), `captureSteps` (étapes exactes pour reproduire l’état à capturer), `urls` (URL d’application face au client et/ou URL de page interne nécessaires pour atteindre cet état) ; extrayez les URL réelles à partir de la description/des commentaires du ticket Jira, du wiki ou des conventions de `open-aso-devmode-url` si elles y sont référencées ; ne fabriquez jamais d’URL).
    - Si `false`, ignorez l’étape 5 pour ce ticket.

## Étape 5 — Porte des médias

S’exécute uniquement lorsque l’étape 4 `mediaNeeded: true` définie. Toutes les dates et heures de
`{state_dir}/media-requests.json` sont UTC ISO-8601 (`date -u +%Y-%m-%dT%H:%M:%SZ`) —
écrivez et comparez toujours dans ce format, de sorte que les calculs de temps écoulé ci-dessous soient sans ambiguïté
à travers les exécutions.

1. `{state_dir}/media-requests.json` une entrée existante pour cette clé de ticket. Si aucune, il s’agit d’une nouvelle requête.
2. **Nouvelle demande :**
   - `mcp__Slack__slack_lookup_user` sur `media.contacts_in_order[0].email` (sandsinh) pour obtenir l’identifiant utilisateur Slack.
   - `mcp__Slack__slack_send_dm` avec un message contenant : la clé du ticket Jira + le lien, exactement ce qu’il faut capturer (`captureSteps`), la ou les URL à utiliser et où la réponse doit aller (« répondez sur le ticket Jira — joignez la capture d’écran directement, ou pour la vidéo, chargez via le formulaire vidéo Experience League habituel et collez le lien `video.tv.adobe.com` obtenu en tant que commentaire »).
   - Écrivez `{state_dir}/media-requests.json[KEY] = {requestedTo: "sandsinh", requestedAt: <UTC ISO-8601 now>, escalated: false}`.
3. **Requête existante :** les deux seuils ci-dessous sont mesurés à partir du `requestedAt` d’origine. L’escalade ne réinitialise pas l’horloge :
   - `now - requestedAt` &lt; `media.escalate_after_hours` -> ne rien faire cette exécution, continuez la publication avec les médias toujours en attente (brouillon PR).
   - `now - requestedAt` >= `media.escalate_after_hours` et pas encore escaladé -> DM `media.contacts_in_order[1]` (kanishka), notes de message sandsinh a déjà été interrogé il y a N heures sans réponse. Mettre à jour l’entrée : `escalated: true, escalatedAt: <UTC ISO-8601 now>`.
   - `now - requestedAt` >= `media.give_up_after_hours` (quel que soit l’état d’escalade) -> définissez `mediaNeeded: false` à des fins de publication, insérez une note intégrée dans le brouillon : `>[!TIP]\n>\n>A screenshot for this step is being added in a follow-up update.` Si un PR existe déjà pour ce ticket et est toujours un brouillon (atteint ici via l’étape 1.4, et non une nouvelle publication de l’étape 6), `git fetch`/extrayez la branche, appliquez la note, validez, envoyez et appelez `gh pr ready <number>` — un brouillon donné doit toujours pouvoir être examiné, et ne pas rester bloqué indéfiniment. Marquez l’entrée `gaveUp: true`.

## Etape 6 — Publier

Ignorer si le ticket a été complètement ignoré à l’étape 3 (rien à publier).

1. `git fetch origin` et `git checkout -B {github.branch_prefix}<KEY>-<short-slug> origin/main` : `-B` (non `-b`), de sorte qu’une branche locale restante d’une exécution précédente bloquée est réinitialisée au lieu de bloquer l’extraction ; le branchement direct depuis `origin/main` supprime également tout état local incorrect d’une exécution précédente au lieu d’y échouer.
2. Écrivez le brouillon de l’étape 4 dans le fichier cible décidé à l’étape 4.3. Vérifiez à nouveau la liste de contrôle « Avant de valider les modifications Markdown » de `experience-league-markdown` ligne par ligne.
3. Si un linter Markdown est configuré (`markdownlint_custom.json` à la racine du référentiel) et que `markdownlint-cli`/`npx markdownlint` est disponible, exécutez-le sur le ou les fichiers modifiés et corrigez les violations avant de les valider.
4. Validation : `docs(aso): <ticket summary, lowercase, no trailing period>\n\nSITES-XXXXX`.
5. `git push -u origin <branch>`.
6. Sélection des réviseurs : `gh pr list --repo {github.repo} --label {github.pr_label} --state open --json reviewRequests` — compter le nombre de réviseurs actuellement répertoriés par chacun des deux réviseurs configurés ; attribuer celui qui en a le moins (égalité -> `sandsinh_adobe`).
7. Corps du PR :

   ```
   ## Summary
   [1-2 sentence description of the feature now documented]
   
   ## Source
   Closes documentation gap tracked in [SITES-XXXXX](https://jira.corp.adobe.com/browse/SITES-XXXXX)
   
   ## Media
   [either "No media needed for this update." OR "Screenshot/video requested from {contact} on {date} — PR opened as draft until resolved." OR "Media follow-up pending — shipped without it; see inline note."]
   
   > 🤖 Drafted by aso-doc-agent
   ```
8. `gh pr create --repo {github.repo} --title "<ticket summary>" --body "<above>" --label {github.pr_label} --reviewer <chosen-github-handle> --draft` si le média est toujours en attente, sinon omettez `--draft`.
9. `gh pr edit <number> --add-label {github.pr_label}` si l’indicateur d’étiquette n’a pas été pris (ceinture et bretelles, correspond au motif utilisé ailleurs dans l’outil de cette organisation).
10. Jira : `add_jira_comment` la liaison de l’URL PR et maintenant, pour la première fois dans cette exécution, ajoutez des `{jira.picked_label}` (`update_jira_issue`, fusionnez avec des libellés existants). C&#39;est la revendication, délibérément appliquée seulement une fois qu&#39;une branche et un PR existent tous les deux : un crash n&#39;importe où dans les étapes 3 à 5 laisse le ticket complètement non étiqueté et récupérable en toute sécurité, au lieu d&#39;être bloqué en permanence. Ne pas faire la transition du statut du ticket — laisser cela au triage de l&#39;équipe de documents ; `{jira.picked_label}` est le seul signal de statut écrit par cet agent.

## Étape 7 — Exécuter le résumé

1. `{state_dir}/run-state.json` de mise à jour : `runs_completed += 1`, horodatage, ticket sélectionné (ou « aucun » + raison), PR ouvert/mis à jour (ou « aucun » + raison), statut de limitation.
2. Imprimez un bref résumé lisible par l’utilisateur (ticket, action entreprise, lien de relations publiques, statut du média).
