---
description: Convertissez les notes de mise à jour internes du sprint ASO au format Experience League destiné aux clients et ajoutez-les à la page des notes de mise à jour.
source-git-commit: d17008c39f231c45a9ba41ca7f0aa96b9878f674
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 0%

---


# Convertisseur de notes de mise à jour

Convertit les notes de mise à jour internes du sprint (à partir du canal de `#aem-sites-optimizer-announcements` Slack ou de la sortie `.cursor/commands/release-notes` Cursor) en une entrée destinée au client et l’ajoute à `help/documentation/release-notes.md`.

## Utilisation

Appelez cette compétence, puis collez le contenu des notes de mise à jour internes lorsque vous y êtes invité. La compétence :

1. Appliquez les instructions ci-dessous pour le filtrage et les règles de tonalité.
2. Analysez les notes de mise à jour internes (sections classées par émoticônes : fonctionnalités ✨, améliorations 🚀, 🤖 AI-First, correctifs 🔧, 🏢 BackOffice).
3. Filtrez toutes les catégories exclues selon les directives (outils d’IA, BackOffice, linter de localisation, tests E2E, éléments SitesInternal uniquement).
4. Réécrivez les éléments restants sur la tonalité destinée au client à l’aide des exemples de tonalité ci-dessous comme référence.
5. Regroupez les éléments associés par domaine de fonctionnalité (et non par équipe ou référentiel).
6. Mettez en forme en tant que nouvelle entrée de version en suivant le modèle de structure de page ci-dessous.
7. Ajoutez la nouvelle entrée à `help/documentation/release-notes.md` (au-dessus de la dernière entrée précédente, sous le paragraphe d’introduction à la page).
8. Imprimer un tableau récapitulatif indiquant : les éléments conservés, les éléments réécrits, les éléments supprimés (avec le motif de chaque élément supprimé).

## Directives

### Principes fondamentaux

1. **Avantage client en premier.** Chaque entrée doit répondre « que puis-je faire maintenant que je ne pouvais pas avant, ou mieux faire ? » — pas « qu&#39;avons-nous expédié ? » Menez avec la valeur , et non l’implémentation.

2. **Ton de leadership.** Écrivez pour un décideur : les résultats et les capacités, pas la mécanique technique. Un vice-président de l’expérience digitale doit immédiatement comprendre pourquoi une mise à jour est importante.

3. **Pas de jargon interne.** Remplacez toutes les formes abrégées internes à l’équipe :
   - « PLG » → « utilisateurs en évaluation » ou « nouveaux clients »
   - « BackOffice » → complètement omis (modification de l’infrastructure uniquement)
   - « MSM » → « AEM Multi-Site Manager »
   - « SHM » → « Moniteur d’intégrité du site »
   - « OrcaFix », « Commandes de curseur », « AGENTS.md » → entièrement omis
   - « EDS » → « Edge Delivery Services »

4. **Entrées courtes.** Une phrase de *quoi*, une phrase de *pourquoi ça compte*. Si les deux correspondent dans une seule phrase, faites-le.

5. **Portée précise.** N’incluez que les modifications qu’un client verra dans l’interface utilisateur du produit ou l’expérience dans ses workflows. Les modifications d’infrastructure, d’outils et d’expérience des développeurs sont exclues.

### Modèle de structure de page

Chaque entrée de version suit cette structure :

```markdown
## [Month Start]–[Day End], [Year]

### New Features

- **[Feature Name]** — [One-sentence benefit statement. One sentence of business context if needed.]

### Enhancements

- **[Enhancement Name]** — [One-sentence improvement statement.]

### Bug Fixes

- [Short description of what was fixed and why it matters to users.]
```

**Règles:**
- Format de période : `May 11–22, 2026` (en-tiret, mois abrégé, année à quatre chiffres).
- Ordre chronologique inverse : dernière version en haut de la page.
- N’incluez que les sections comportant du contenu. Omettez les options « Améliorations » ou « Correctifs de bugs » si elles sont vides.
- Les entrées de correctifs n’utilisent pas de noms de fonctionnalités en gras, mais des puces simples.
- N’incluez les correctifs que s’il existe au moins 3 correctifs visibles par l’utilisateur.

### Éléments à inclure ou à exclure

**Inclure:**

| Catégorie | Exemples |
|---|---|
| Nouveaux types d’opportunités | Incohérence de l’intention de publicité, pas de CTA au-dessus du pli |
| Nouveaux affichages ou workflows | Onglet Déployé, exportation CSV, liaison Jira |
| Améliorations de la version d’essai/d’intégration | Flux de configuration guidé, statut intégré sur site |
| Améliorations des paramètres | URL de la cible d’audit, configuration du type de diffusion |
| Correctifs d’expérience utilisateur significatifs | Nombre incorrect, navigation interrompue, problèmes d’affichage affectant les décisions |
| Nouvelles données/intégrations | Données Ahrefs dans la recherche organique, arborescence de dépendances dans la sécurité |
| Fonctionnalités de déploiement vers l’auteur | Nouveaux types d’opportunités qui prennent en charge le déploiement direct |

**Exclure:**

| Catégorie | Pourquoi ? |
|---|---|
| Outils d’IA (OrcaFix, commandes de curseur, AGENTS.md, règles de code Claude) | Outils de développement internes, non visibles par les clients |
| Sélecteur de localisation/hooks de pré-validation | Processus d’ingénierie, et non fonctionnalité du produit |
| Modifications du back-office/de l’infrastructure | Non visible dans l’interface utilisateur sauf si elle modifie le comportement de l’utilisateur final |
| Mises à niveau de la version de React Spectrum | Dépendance interne, non visible par l’utilisateur |
| Améliorations des tests E2E | La qualité technique, pas une caractéristique du produit |
| Automatisation du pipeline de publication | Processus interne |
| Fonctionnalités SitesInternal uniquement | Non disponible pour les clients |

### Exemples de tons

| Expression interne | Formulation destinée aux clients |
|---|---|
| « Ajout de l’état REJETÉ pour le workflow de validation manuelle » | « Vous pouvez désormais marquer les suggestions comme rejetées afin d’indiquer qu’elles ne s’appliquent pas à votre site, ce qui permet de concentrer votre liste d’opportunités sur des éléments exploitables. » |
| « Vue déployée pour les opportunités canoniques et Hreflang (regroupées par date) » | « Les modifications apportées aux opportunités canoniques et Hreflang sont désormais regroupées par date de déploiement dans un onglet Déployé , ce qui vous donne un historique clair de ce qui a été corrigé et quand. » |
| « Texte de remplacement Autofix V2 — Évaluation avant vol de la possibilité de vérifier la fixabilité » | « Avant de déployer un correctif Texte de remplacement, vous pouvez exécuter une vérification en amont pour vérifier que le correctif peut être appliqué à votre contenu. » |
| « Optimisation du stockage à 96 % pour les mesures SHM » | omettre — infrastructure uniquement |
| « AGENTS.md avec rôles d’agent formels et mécanismes de sécurisation » | omettre — outil d’IA interne |
| « Optimisations des performances des tests E2E (~6 min → ~5 min) » | omettre — processus d&#39;ingénierie |

### Règles de regroupement

- **Regroupez-les par domaine de fonctionnalité** et non par équipe ou référentiel. Par exemple, toutes les améliorations apportées au texte de remplacement (fonctionnalités, améliorations et correctifs) appartiennent à la même zone ; ne les répartissez pas entre les sections.
- **Regroupez les correctifs étroitement liés** en une seule puce plutôt que de les répertorier séparément (par exemple, « Plusieurs améliorations d’affichage et de disposition dans les opportunités de trafic payant, d’accessibilité et de sécurité »).
- **Section Seuil pour les correctifs de bugs** : incluez cette section uniquement lorsqu’il existe 3 correctifs visibles par l’utilisateur ou l’utilisatrice ou plus qui méritent d’être signalés. Les corrections mineures ou purement cosmétiques en dessous de ce seuil doivent être omises.

## Étapes

1. Appliquez les directives de ce fichier : internalisez tous les principes, incluez/excluez les règles, les exemples de tonalité et les règles de regroupement.
2. Demandez à l’utilisateur la période couverte (par exemple, « 11-22 mai 2026 ») si elle n’est pas déjà fournie.
3. Demandez à l’utilisateur de coller le contenu des notes de mise à jour internes (ou d’accepter un chemin d’accès au fichier).
4. Traitez le contenu :
   - **Analysez** chaque section (✨/🚀/🤖/🔧/🏢) et ses puces.
   - **Filtrer** selon le tableau Exclure ci-dessus. Marquez chaque élément déposé avec un motif.
   - **Réécrire** les éléments conservés dans le ton client : avantage d’abord, pas de jargon, entrées courtes.
   - **Regrouper** par domaine de fonctionnalité où plusieurs éléments sont associés.
   - **Vérification du seuil** : incluez uniquement une section « Correctifs de bugs » s’il existe plus de 3 correctifs visibles par l’utilisateur.
5. Mettez en forme la nouvelle entrée à l’aide du modèle de structure de page ci-dessus.
6. Lire le contenu actuel de `help/documentation/release-notes.md`.
7. Insérez la nouvelle entrée immédiatement après le paragraphe d’introduction à la page (avant le dernier en-tête de date de `##` précédent).
8. Écrivez le fichier mis à jour.
9. Imprimer le tableau récapitulatif.

## Format d’entrée

La compétence accepte les notes de mise à jour internes au format d’équipe standard :

```
*ASO UI Release Notes — [Date Range]*
Collaborators: [teams]

✨ *Features*
• [Feature description]

🚀 *Enhancements*
• [Enhancement description]

🤖 *AI-First Development*
• [AI tooling items — will be dropped]

🔧 *Fixes & UX Improvements*
• [Fix description]

🏢 *BackOffice*
• [BackOffice items — will be dropped]
```

## Sortie

Les sorties de compétence :

1. Entrée formatée destinée aux clients (à réviser avant la rédaction).
2. Une invite de confirmation avant de modifier les `release-notes.md`.
3. Après l’écriture : un tableau récapitulatif des éléments conservés/réécrits/supprimés.
