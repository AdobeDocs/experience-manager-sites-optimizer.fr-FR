---
source-git-commit: ed1960cc0364dc4169a454a4860b7463890e3b74
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 0%

---
# Agent de document ASO — Utilisation

Qu’est-ce que c’est, comment cela fonctionne et que faire quand il a besoin de vous ?

## Effets

Chaque jour, cet agent sélectionne la fonctionnalité ASO non documentée la plus prioritaire parmi
[liste d’attente de SITES-49539](https://jira.corp.adobe.com/browse/SITES-49539) (39 tickets, par ex.
« Comment faire pour une opportunité canonique », « Notifications Slack »), écrit un élément de documentation
pour ce faire, dans le style maison de ce référentiel, et ouvre une requête de tirage — attribuant l’une des deux options
le nombre de réviseurs configurés (`sandsinh_adobe`/`kanishka_adobe`) actuellement ouverts est inférieur
examiner les demandes de cet agent. Si la fonction a besoin d’une capture d’écran ou d’une vidéo, elle demande :
un sur Slack avant de terminer la RP.

Chaque exécution vérifie également le statut de révision sur chaque requête de tirage ouverte : les requêtes de tirage approuvées sont fusionnées
immédiatement, et les commentaires des modifications demandées sont lus et, lorsqu’ils peuvent être généralisés
leçon (pas une faute de frappe ponctuelle), enregistrée afin que les versions ultérieures ne répètent pas la même erreur.

Une exécution = une fonctionnalité = au plus une requête de tirage. Il ne touche jamais plus d&#39;un ticket par course,
et n’ouvre jamais plus de 3 PR à la fois (attend que ceux qui existent soient fusionnés/fermés en premier).

## Où tout habite

| Quoi | Chemin d’accès |
|---|---|
| Comment il décide de ce qu’il doit faire | `.claude/skills/aso-doc-agent/SKILL.md` |
| La procédure pas à pas exacte | `.claude/skills/aso-doc-agent/references/pipeline.md` |
| Paramètres spécifiques à l’équipe (modifiez ceci pour modifier les réviseurs, la limite, le délai d’escalade) | `.claude/skills/aso-doc-agent/config.yml` |
| Leçons tirées des commentaires de l’examen de la fonctionnalité de RP (suivies dans Git, lues avant chaque brouillon) | `.claude/skills/aso-doc-agent/references/review-learnings.md` |
| État d&#39;exécution local (gitignored — supprime en toute sécurité, reconstruit) | `.claude/skills/aso-doc-agent/state/` |
| Programme d’installation du planning quotidien | `.claude/scripts/aso-doc-agent-setup.sh` |
| Liste autorisée des autorisations pour les exécutions découplées | `.claude/settings.local.json` (gitignored, machine-local) |

## En cours d’exécution

- **Manuellement, dans une session normale :** `/aso-doc-agent` (ou `/aso-doc-agent --ticket SITES-XXXXX`)
- **Headless, unique :** `claude -p "/aso-doc-agent"` de la racine du référentiel
- **Quotidien, sans surveillance :** déjà installé via `launchctl` (voir ci-dessous) — s’exécute à 7h53, heure locale, tous les jours, aucune action n’est nécessaire

### Installer/modifier le planning quotidien

```bash
bash .claude/scripts/aso-doc-agent-setup.sh
```

Installe une tâche de `launchd` (`~/Library/LaunchAgents/com.sandsinh.aso-doc-agent.plist`) qui
s’exécute `claude -p "/aso-doc-agent"` à partir de ce référentiel quotidiennement. Exécutez à nouveau le script chaque fois que vous
modifiez le planning qu’il contient (par défaut : 07:53 local). Cela ne fonctionne que lorsque votre ordinateur est
activé et réactivé à ce moment : launch n’exécute pas les tâches manquantes de manière rétroactive, mais les exécutera
l’heure planifiée suivante normalement.

```bash
launchctl list | grep com.sandsinh.aso-doc-agent   # confirm it's loaded
launchctl start com.sandsinh.aso-doc-agent         # trigger a run right now, don't wait for 07:53
launchctl unload ~/Library/LaunchAgents/com.sandsinh.aso-doc-agent.plist  # stop it
```

Les journaux de chaque exécution planifiée se posent dans `.claude/skills/aso-doc-agent/state/launchd.out.log`
et `launchd.err.log`.

## Ce qu&#39;on vous demandera de faire

- **Un DM Slack de l’agent** (envoyé en tant que vous, à vous - sandsinh d’abord, kanishka après
escalade) demandant une capture d’écran ou une vidéo, avec les étapes de capture exactes et les URL pour
utilisez . **Répondez sur le ticket Jira associé, mais pas dans Slack** : joignez directement la capture d’écran,
ou pour la vidéo, chargez-la via le formulaire vidéo Experience League habituel.
(`experience-league-video-upload` des compétences) et collez le résultat `video.tv.adobe.com`
lien sous forme de commentaire Jira. La prochaine exécution le récupère automatiquement.
- Si personne ne répond dans les **5 jours**, la demande passe de sandsinh à kanishka
automatiquement. Après **10 jours** sans réponse de l’un ou l’autre, l’agent envoie le document
sans média et ajoute une note intégrée. Il n’y a pas de fusion automatique basée sur le délai d’expiration : la requête de tirage
attend toujours un véritable examen humain, quel que soit le temps que cela prend.
- **Une RP à réviser** — affectée à celui d&#39;entre vous deux qui a moins de RP ouverts par l&#39;agent
en attente de révision. Les brouillons de rapports d’information signifient que les médias sont toujours en attente ; ils basculent vers
prêt pour la révision automatiquement une fois la ressource affichée. Validez-le et l&#39;agent fusionne
pour la prochaine exécution, aucune étape de fusion distincte n’est nécessaire de votre part.
- **Si vous demandez des modifications** l’agent lit vos commentaires lors de l’exécution suivante. Généralisable
les commentaires (et non les correctifs de faute de frappe ou de lien) sont écrits vers `references/review-learnings.md` afin que le
la même correction n’a pas besoin d’être répétée sur une requête de tirage ultérieure.

## Ajustement du comportement

Modifier les `.claude/skills/aso-doc-agent/config.yml` (suivies dans Git — les modifications ont une incidence sur chaque
exécution future, sur cette machine ou sur celle de toute autre personne qui clone le référentiel) :

- `pr.max_open` : nombre de PR ouvertes avant que l&#39;agent ne mette en pause le prélèvement de nouveaux tickets (3 par défaut)
- `pr.stale_after_hours` — la durée pendant laquelle un `CHANGES_REQUESTED` PR peut rester assis avant d&#39;arrêter de compter vers `pr.max_open` (par défaut 336 = 14 jours) ; il reste ouvert, ce qui ne fait que débloquer de nouveaux choix
- `github.reviewers` — qui est affecté, et dans quel équilibre
- `media.contacts_in_order` / `escalate_after_hours` (par défaut 120 = 5 jours) / `give_up_after_hours` (par défaut 240 = 10 jours) — qui est interrogé, dans quel ordre et avec quelle patience ; les deux sont mesurées à partir de la demande initiale, de sorte que l&#39;escalade ne repousse pas la date d&#39;abandon
- `pr.check_reviews_every_run` : désactivez l&#39;étape de vérification (non recommandé ; c&#39;est ainsi que les fusions et les apprentissages se produisent)

## S’il se bloque sur une invite d’autorisation

Les exécutions découplées (`claude -p`, lancées) n’ont pas de terminal à inviter — un appel d’outil non répertorié
échouera au lieu de pendre. Si le journal d’une exécution affiche un refus d’autorisation pour une commande
le pipeline a légitimement besoin de , ajoutez-le à la liste `permissions.allow` dans .
`.claude/settings.local.json` (non suivi dans git — machine-local ; chaque développeur exécutant
cet agent a besoin de sa propre copie avec sa propre portée (place sur la liste autorisée).

## S’il cesse de progresser entièrement

Vérifiez, dans l’ordre :
1. `gh pr list --repo Adobe-Enterprise-Docs/experience-manager-sites-optimizer.en --label aso-doc-agent --state open` — si l&#39;affichage est 3, il est en attente d&#39;avis, pas bloqué.
2. Jira : reste-t-il un ticket de `New` éligible sous SITES-49539 qui n’est pas déjà `aso-doc-agent-picked` ? Le libellé n’est appliqué qu’une seule fois qu’un branch+PR existe (pipeline.md Étape 6.10), de sorte qu’une exécution bloquée ne devrait pas laisser un ticket étiqueté mais dépublié — si vous en trouvez toujours un (par exemple un libellé ajouté manuellement), supprimez-le manuellement pour rendre le ticket éligible à nouveau.
3. `.claude/skills/aso-doc-agent/state/launchd.err.log` l’erreur de l’exécution la plus récente.
4. Si le résumé d’une exécution indique « liste d’attente épique entièrement couverte » ou « rien à faire ici » mais que vous savez qu’il doit y avoir du travail éligible, traitez cela comme suspect ; ces messages sont réservés aux résultats véritablement vides. Une erreur Jira/GitHub/Slack réelle est consignée séparément et doit s’afficher comme sa propre ligne dans `launchd.err.log` au lieu de se cacher derrière l’un de ces messages.
