---
name: experience-league-video-upload
description: 'À utiliser lorsqu’un utilisateur souhaite envoyer/charger une vidéo dans Experience League (envoi de vidéo video.tv.adobe.com/KT) pour l’incorporer via >[!VIDEO] dans le markdown de ce référentiel : cette section couvre le remplissage du formulaire d’envoi avec l’automatisation du navigateur, les valeurs par défaut de ce référentiel et ce qui ne doit jamais être automatisé.'
source-git-commit: 14f10c231373992c49a8bb93c043556305b6280d
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 1%

---


# Chargement vidéo Experience League

## Vue d’ensemble

Les vidéos Experience League ne sont pas hébergées dans ce référentiel. Un `.mp4` local est chargé via un formulaire d’envoi distinct, qui renvoie une URL `video.tv.adobe.com` que vous incorporez ensuite avec `>[!VIDEO](...)` (voir [[experience-league-markdown]]). Cette compétence remplit ce formulaire via l’automatisation du navigateur, jusqu’à ce que (sans inclure) le fichier soit joint et envoyé.

Formulaire : https://81368-exlmpcvideoupload.adobeio-static.net/#/

## Recommandations relatives aux fichiers vidéo

Avant d’enregistrer ou de sélectionner un élément, recommandez un format **16:9** avec une résolution **maximale de 1 920 x 1 080 pixels** — il s’agit de l’exigence énoncée du formulaire, et non pas simplement d’une préférence de style. Mentionnez-le de manière proactive (par exemple, lorsqu’un utilisateur dit qu’il est sur le point de capturer un enregistrement d’écran à cette fin), et pas seulement si cela lui est demandé.

## Règle stricte : ne jamais joindre de fichier ni soumettre

L’envoi crée un vrai ticket KT Jira et le transfère vers la plateforme vidéo de production, une action tournée vers l’extérieur et difficile à inverser. **Toujours** arrêtez-le une fois qu’un champ sur deux est rempli et remettez-le à l’utilisateur ou à l’utilisatrice pour le fichier vidéo et le dernier clic d’envoi, même s’il ou elle ne répète pas l’instruction la prochaine fois. Il s’agit de la valeur par défaut pour cette compétence, et non d’un élément qui doit être reconfirmé par demande. Ignorez uniquement cet arrêt si l’utilisateur indique explicitement de soumettre pour lui dans cette même demande.

## Conditions préalables

Nécessite le serveur MCP `chrome-devtools`, qui n’est **pas** validé dans ce référentiel (un MCP d’automatisation du navigateur ne doit pas être forcé sur chaque contributeur). S’il n’est pas chargé :

1. Créez des `.mcp.json` à la racine du référentiel :

   ```json
   {
     "mcpServers": {
       "chrome-devtools": {
         "command": "npx",
         "args": ["-y", "chrome-devtools-mcp@latest", "--accept-insecure-certs", "--no-usage-statistics"]
       }
     }
   }
   ```
2. Ajoutez des `.mcp.json` à `.gitignore` (outils personnels, non partagés).
3. Dans `.claude/settings.local.json`, ajoutez `"enableAllProjectMcpServers": true` et `"enabledMcpjsonServers": ["chrome-devtools"]`.
4. Indiquez à l&#39;utilisateur de redémarrer Claude Code (ou d&#39;exécuter `/mcp`) — Les serveurs MCP ne se chargent qu&#39;au démarrage, ce qui ne peut pas être fait en milieu de session.

## Valeurs par défaut de ce référentiel

Sauf indication contraire de l’utilisateur ou de l’utilisatrice, utilisez :

| Field (Champ) | Par défaut | Pourquoi ? |
|---|---|---|
| Cloud | `Experience Cloud` | — |
| Produit | `AEM` | Valeur par défaut spécifiée par l’utilisateur pour ce référentiel (le formulaire répertorie également `AEM as a Cloud Service` — ne le remplacez pas, sauf demande contraire). |
| Sous-produit | `AEM Sites` | Correspondance la plus proche ; le formulaire ne comporte aucune entrée « Sites Optimizer » |
| Rôles | `User` | Le contenu de contrôle en amont/Sites Optimizer est destiné aux auteurs et aux spécialistes du marketing, et non aux administrateurs et aux développeurs, sauf si la vidéo est clairement destinée à une audience technique |
| Niveaux de compétence | `Beginner` | Sauf si le workflow affiché comporte de vraies conditions préalables |
| Sexe de la ou des voix vidéo | `No voices` | Uniquement pour les enregistrements sur écran silencieux — demander si le clip contient une narration |
| Type de vidéo | Demander ou déduire à partir du contenu | Les options en direct sont `Event` / `Feature` / `Technical` / `Value`. Une présentation de l’interface utilisateur est généralement `Feature`. |
| E-mail | tout ce qui est pré-rempli | Le formulaire remplit automatiquement l’e-mail Adobe de l’utilisateur connecté ; ne le remplacez pas |

## Étapes

1. `mcp__chrome-devtools__new_page` à l’URL du formulaire.
2. `mcp__chrome-devtools__take_snapshot` et patientez (`mcp__chrome-devtools__wait_for` le `"Title"`) jusqu’à ce que le chargement des données de formulaire soit terminé — il commence par « Chargement des données de formulaire... » filante.
3. Remplir **Titre** et **Description** — La description est une zone de texte enrichi modifiable par du contenu, et non une `<textarea>` simple. `fill`/`fill_form` s’y trouvent silencieusement sans opération (la valeur n’est pas prise et l’erreur « requis » reste). Au lieu de cela : `click`-le pour qu’il se concentre, puis `mcp__chrome-devtools__type_text` avec le texte.
4. Les listes déroulantes (**Type de vidéo**, **Genre de voix(s) vidéo**, **Cloud**, **Produit**, **Sous-produit**, **Nom de l’événement**) sont des boutons de zone de liste personnalisés, et non des `<select>` natifs. Pour chacun d&#39;eux : `click` le bouton pour l&#39;ouvrir, lisez les options réelles de l&#39;instantané (elles sont chargées API — ne supposez pas que l&#39;orthographe exacte de l&#39;option par défaut du tableau est toujours à jour), puis `click` le `option` correspondant.
5. **Produit** et **Sous-produit** sont désactivés jusqu’à ce que leur champ parent soit défini (le produit a besoin de Cloud ; le sous-produit a besoin de Produit) - remplissez-les dans cet ordre.
6. **Rôles** et **Niveaux de compétence** sont des groupes de cases à cocher — `fill_form` avec `"value": "true"` sur la case à cocher `uid` fonctionne ici correctement (contrairement au champ de description).
7. Arrêtez. Effectuez une capture d’écran, résumez ce qui a été défini et pourquoi (en particulier toute valeur par défaut qui a été remplacée, comme un produit/sous-produit), et dites à l’utilisateur de joindre la vidéo et de s’envoyer.
8. Une fois que l’utilisateur a indiqué l’avoir envoyé, demandez-lui l’URL de la vidéo Adobe MPC obtenue (affichée sur le formulaire après le chargement, par exemple `https://video.tv.adobe.com/v/3496629?learn=on`). Utilisez-le pour renseigner le numéro court de la `>[!VIDEO](...)` où cette vidéo était censée aller - ne fabriquez pas et ne devinez pas vous-même l’URL/l’ID.

## Validation d’une URL de vidéo renvoyée

Chaque fois qu’un utilisateur vous remet une URL de vidéo à incorporer (étape 8 ci-dessus ou à tout autre moment) :

- **Rejeter tout ce qui ne figure pas sur `video.tv.adobe.com`.** Les vidéos doivent y être hébergées selon [[experience-league-markdown]] — un lien vers YouTube, un hôte de fichier ou tout autre domaine n’est pas une cible `>[!VIDEO]` valide. Indiquez à l’utilisateur qu’il doit d’abord passer par le flux de chargement de ce référentiel ; ne l’incorporez pas.
- **S’il s’agit d’une URL de `video.tv.adobe.com` valide dont l’`&enablevpops` est manquante** ajoutez-la avant de l’incorporer (correspond à la convention déjà utilisée par tous les autres `>[!VIDEO]` de ce référentiel - voir `help/home.md`, `help/documentation/trial.md`, etc.). Ajoutez `&enablevpops` s’il existe déjà un `?`, sinon `?enablevpops`.

## Erreurs courantes

- En `fill`/`fill_form` sur le champ Description et en continuant lorsque la bannière d’erreur affiche toujours « Une description est requise ». — vérifiez la liste des erreurs après chaque étape, pas seulement à la fin.
- Deviner le texte de l’option de liste déroulante à partir de la mémoire au lieu d’ouvrir la liste déroulante : les valeurs réelles (par exemple, `No voices` pour le genre de la voix, `Feature`/`Technical`/`Value` pour le type de vidéo, la répartition AEM/AEM-as-a-Cloud-Service sous Produit) ne peuvent pas être devinées et changent indépendamment de ce document.
- Cliquez sur **Télécharger une vidéo** / en joignant un fichier « pour enregistrer une étape pour l’utilisateur ». Ne pas utiliser — voir la règle Hard ci-dessus.
