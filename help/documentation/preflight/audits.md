---
title: Exécuter des audits dans le contrôle en amont
description: Découvrez comment démarrer un audit de contrôle en amont sur votre page.
source-git-commit: 14f10c231373992c49a8bb93c043556305b6280d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 17%

---


# Audits dans le contrôle en amont

Le contrôle en amont effectue un audit de votre page afin d’identifier les opportunités d’amélioration de votre contenu avant sa publication. Contrairement à une analyse automatique, vous choisissez quand exécuter les audits, de sorte que vous pouvez analyser une page chaque fois que vous êtes prêt.

![Écran d’atterrissage de contrôle en amont avec le bouton Analyser la page &#x200B;](./assets/audits/hero.png){align="center"}

Pour exécuter des audits de contrôle en amont sur une page :

1. Ouvrez la page à auditer dans votre [environnement de création](./access-preflight.md) (éditeur universel, création basée sur les documents ou éditeur de page AEM Sites).
1. Ouvrez le [panneau Contrôle en amont &#x200B;](./access-preflight.md). Le contrôle en amont s’ouvre sur l’écran d’entrée **Exécuter l’audit de préparation des performances**.
1. Sélectionnez **Analyser la page**. Le contrôle en amont exécute tous ses audits sur la page active et ouvre le tableau de bord de préparation, où il affiche un score de préparation et les opportunités qu’il détecte, regroupés par catégorie.

Pour comprendre les résultats de la prévisualisation et identifier les opportunités d’optimisation, consultez [Résultats d’audit en contrôle en amont](./audit-results.md).

## Utiliser le bouton de contrôle en amont intégré

Si votre environnement de création exécute [AEM 2026.7.0 (version 27083)](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/maintenance/2026/2026-7-0#release-27083) ou une version ultérieure, le contrôle en amont est intégré à la barre d’outils de l’éditeur de page d’AEM Sites. Sélectionnez l’icône **Contrôle en amont** (le bouton de lecture) pour ouvrir le panneau de la page active, puis sélectionnez **Analyser la page** pour exécuter les audits.

>[!VIDEO](https://video.tv.adobe.com/v/3496629?learn=on&enablevpops)

## Poursuivre une session précédente

Le contrôle en amont mémorise votre exécution la plus récente, de sorte que vous n’ayez pas à relancer les audits si vous quittez et revenez.

* Si vous rouvrez le panneau Contrôle en amont dans le **même onglet du navigateur** y compris après une actualisation, le contrôle en amont charge automatiquement les résultats de votre dernière exécution.
* Si vous revenez **dans un nouvel onglet ou après la fermeture du navigateur**, l’écran d’entrée affiche un bouton **Continuer la dernière session** en regard de **Analyser la page**. Sélectionnez **Continuer la dernière session** pour recharger vos résultats les plus récents, ou sélectionnez **Analyser la page** pour démarrer une nouvelle exécution.

Le contrôle en amont effectue le suivi de la dernière exécution séparément pour chaque page. Par conséquent, la **Continuer la dernière session** recharge toujours la dernière exécution pour la page sur laquelle vous vous trouvez.

Une fois les audits terminés et les résultats affichés, sélectionnez **Réanalyser** dans le **Autres actions** (**...**) dans la barre d’outils pour ignorer les résultats et réexécuter chaque audit. Voir [&#x200B; Résultats de l’audit en contrôle en amont &#x200B;](./audit-results.md#toolbar).

