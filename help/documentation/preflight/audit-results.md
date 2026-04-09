---
title: Résultats de l’audit dans le contrôle en amont
description: Découvrez comment interpréter les résultats de l’audit de contrôle en amont et la barre de progression de l’utilisateur, accéder aux problèmes dans l’aperçu et appliquer les suggestions générées par l’IA.
source-git-commit: 10534d1fabdd88b11f45895d39bc1afd0d664ff1
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Résultats de l’audit dans le contrôle en amont

Une fois l’audit terminé, le contrôle en amont affiche les résultats de l’audit sous forme d’opportunités. Chaque opportunité est organisée par type et comprend des recommandations pour vous aider à améliorer et optimiser la page. Dans une opportunité, les problèmes individuels identifient les éléments spécifiques à examiner ou à corriger.

En haut de la boîte de dialogue de contrôle en amont d’AEM se trouve une barre de Progression de l’utilisateur qui reflète les résultats d’audit globaux. Il indique le pourcentage d’opportunités qui se sont passées sans problème, ainsi que le nombre total d’problèmes trouvés pour toutes les opportunités. La barre de progression de l’utilisateur permet aux auteurs d’évaluer rapidement l’intégrité globale de la page.

![Barre de progression des utilisateurs et opportunités d’audit dans la boîte de dialogue de contrôle en amont d’AEM](./assets/overview/hero.png){align="center"}

La barre a un code couleur :

* Rouge pour **moins de 1/3** des opportunités terminées
* Orange pour **1/3 à 2/3 complet**
* Vert pour **plus de 2/3 complet**
* Bleu pendant que les audits sont **toujours en cours**

Consultez la [liste complète des types d’opportunités disponibles et comment les traiter](./overview.md#preflight-opportunities).

## Accéder aux problèmes et appliquer des suggestions

Une fois l’audit terminé, vous pouvez passer rapidement aux problèmes identifiés et appliquer les suggestions générées par l’IA directement dans l’aperçu.

![Mise en surbrillance de l’aperçu du contrôle et panneau de suggestions de l’IA](./assets/audit-results/highlight-issue.png){align="center"}

### Accès à un événement

1. Sélectionnez un événement dans la liste des événements du panneau Contrôle en amont.
1. L’aperçu fait automatiquement défiler la page jusqu’à l’emplacement correspondant et le met en surbrillance, afin que vous puissiez examiner le problème en contexte sans le rechercher manuellement.

### Appliquer les suggestions générées par l’IA

Pour les problèmes qui incluent des recommandations générées par l’IA, vous pouvez appliquer les optimisations suggérées directement à partir du panneau de suggestions.

#### Application d’une optimisation

1. Examinez la suggestion générée par l’IA.
1. Sélectionnez **Appliquer l’optimisation**.

Le contenu recommandé est directement appliqué au contenu.

#### Modifier avant l’application

Si des ajustements sont nécessaires :

1. Modifiez la suggestion générée par l’IA dans le panneau de suggestions.
1. Sélectionnez **Appliquer l’optimisation**.

La version modifiée est appliquée à l’aperçu.
