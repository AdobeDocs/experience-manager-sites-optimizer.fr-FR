---
title: Résultats de l’audit dans le contrôle en amont
description: Découvrez comment interpréter les résultats de l’audit de contrôle en amont, le compteur de préparation et les catégories d’audit, et accédez aux opportunités dans l’aperçu.
source-git-commit: f19dd2eec5cef95f406111d2250ff1101a4fd430
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 5%

---


# Résultats de l’audit dans le contrôle en amont

Une fois les audits terminés, le contrôle en amont affiche les résultats dans le tableau de bord de préparation. Le tableau de bord présente un indicateur de préparation globale et les opportunités trouvées, regroupées par catégorie d’audit. Au sein de chaque catégorie, les audits individuels identifient des éléments spécifiques à examiner ou à corriger.

## Compteur de préparation

En haut du tableau de bord, le compteur de préparation reflète les résultats d’audit globaux. Il affiche un score de préparation sous forme de pourcentage, en fonction de la proportion d’audits qui se sont terminés sans opportunités, ainsi que le nombre total d’opportunités trouvées dans tous les audits. Le compteur de préparation vous permet d’évaluer l’état de santé global de la page en un coup d’œil.

![Compteur de préparation et catégories d’audit dans le tableau de bord Contrôle en amont](./assets/overview/hero.png){align="center"}

Pendant que les audits sont toujours en cours, le compteur de préparation affiche une barre de progression avec un statut tel que **Audits en cours d’exécution** ou le nombre d’audits toujours en cours. Une fois les audits terminés, le compteur affiche le pourcentage de préparation final et le nombre d’opportunités.

## Catégories d’audit

Le contrôle en amont regroupe les audits associés dans des catégories, telles que **SEO** et **Accessibilité**. Chaque catégorie s’affiche sous la forme d’une carte qui indique le nombre d’opportunités trouvées ou indique que tous ses audits ont réussi sans opportunité.

Développez une catégorie pour afficher ses audits individuels. Chaque audit indique s’il a réussi ou trouvé des opportunités, une brève description et un nombre d’opportunités trouvées. Sélectionnez un audit qui a trouvé des opportunités d’ouvrir sa page de détails.

Pour obtenir la liste complète des catégories d&#39;audit et les audits de chacune d&#39;elles, voir [Catégories d&#39;audit de contrôle en amont](./overview.md#preflight-audit-categories).

## Détails de l’opportunité

La page des détails affiche les opportunités trouvées par l’audit sélectionné. Lorsque le même problème se produit à plusieurs endroits, chaque occurrence est appelée instance . Utilisez le navigateur (**Instance précédente** et **Instance suivante**) pour les parcourir. Il indique votre position, par exemple *1 des 5 instances trouvées*.

![Page de détail d’un audit, présentant une opportunité et sa suggestion](./assets/audit-results/audit-detail.png){align="center"}

Chaque opportunité comprend :

* Badge de gravité ou d’impact indiquant l’importance de l’opportunité.
* Détails sur l’opportunité, tels qu’une description du problème, une recommandation et, pour l’accessibilité, la règle WCAG associée et le niveau de conformité.
* Une section **Élément** qui affiche l’élément concerné sur la page, avec un bouton **Mettre en surbrillance sur la page**.
* Une section **Suggestion** avec un correctif recommandé. Lorsque la suggestion est générée par l’IA, elle est marquée comme étant générée par l’IA et peut inclure une brève justification expliquant la correction suggérée.

## Surligner sur la page

Une fois les audits terminés, vous pouvez rapidement localiser et comprendre une opportunité en la mettant en surbrillance directement sur la page.

Le contrôle en amont met en surbrillance l’élément concerné dans son contexte et connecte le résultat du panneau à l’emplacement exact dans votre contenu. Il est ainsi plus facile de vérifier et de résoudre les opportunités sans effectuer de recherche manuelle dans la page.

1. Ouvrez le panneau Contrôle en amont dans le contexte de la page à contrôler, puis sélectionnez **Analyser la page** pour exécuter les contrôles.
1. Sélectionnez un audit dans le tableau de bord de préparation, puis sélectionnez une opportunité à examiner.
1. Sélectionnez **Mettre en surbrillance sur la page**. L’aperçu fait automatiquement défiler la page jusqu’à la zone appropriée et met en surbrillance l’élément correspondant, afin que vous puissiez facilement identifier et optimiser l’opportunité en contexte.

## Identifiant du traitement

Chaque exécution de contrôle en amont possède un identifiant de tâche unique, affiché au bas du panneau. Elle s’avère principalement utile lorsqu’un administrateur résout un problème d’exécution spécifique. Pointez sur l’ID et sélectionnez l’icône Copier qui s’affiche à droite ; l’ID est copié dans le presse-papiers et un message de confirmation s’affiche. Incluez cet identifiant lorsque vous signalez un problème.
