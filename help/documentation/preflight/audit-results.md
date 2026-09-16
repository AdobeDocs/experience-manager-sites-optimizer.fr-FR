---
title: Résultats de l’audit dans le contrôle en amont
description: Découvrez comment interpréter les résultats de l’audit de contrôle en amont, le compteur de préparation et les catégories d’audit, et accédez aux opportunités dans l’aperçu.
source-git-commit: dd2637e61e15a6b8364456ae7d11717a0b81ad09
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 2%
---

# Résultats de l’audit dans le contrôle en amont

Une fois les audits terminés, le contrôle en amont affiche les résultats dans le tableau de bord de préparation. Le tableau de bord présente un indicateur de préparation globale et les opportunités trouvées, regroupées par catégorie d’audit. Au sein de chaque catégorie, les audits individuels identifient des éléments spécifiques à examiner ou à corriger.

## Barre d’outils

La barre d’outils située en haut du tableau de bord de préparation fournit des actions pour l’exécution en cours :

* **Réanalyser** - Lancez une toute nouvelle exécution d’audit sur la page active. L’option Réanalyser ignore toujours les résultats affichés et exécute à nouveau chaque audit. Vous devez donc l’utiliser chaque fois que vous souhaitez de nouveaux résultats, par exemple, après avoir modifié la page. La réanalyse se trouve dans le **Autres actions** (**...**) menu.
* **Exporter** - Téléchargez l’exécution actuelle au format **CSV** (feuille de calcul conviviale) ou **PDF** (document formaté). En fonction de votre environnement, sélectionnez **Exporter** dans la barre d’outils ou dans l’**Autres actions** (**...**) menu.

Lors de l’exportation, vous pouvez également choisir les éléments à inclure :

* **Inclure le tableau des métadonnées** - Ajoutez un tableau des détails d’exécution, tels que les détails de l’hôte, du chemin de contenu et de la génération.
* **Inclure les audits réussis** - Inclure les audits réussis sans opportunités, pas seulement les opportunités trouvées.

>[!NOTE]
>
>Les exportations PDF sont toujours générées en anglais, quelle que soit la langue de l’interface. Les exportations de fichiers CSV suivent votre langue d’interface aussi étroitement que possible.

## Compteur de préparation

En haut du tableau de bord, le compteur de préparation reflète les résultats d’audit globaux. Il affiche un score de préparation sous forme de pourcentage, en fonction de la proportion d’audits qui se sont terminés sans opportunités, ainsi que le nombre total d’opportunités trouvées dans tous les audits. Le compteur de préparation vous permet d’évaluer l’état de santé global de la page en un coup d’œil.

![Compteur de préparation et catégories d’audit dans le tableau de bord Contrôle en amont](./assets/overview/hero.png){align="center"}

Lorsque vous affichez une exécution qui a été rechargée à partir d’une session précédente, l’en-tête indique la durée de son exécution (par exemple, *hier*. Pour plus d’informations, voir [Poursuivre une session précédente](./audits.md#continue-a-previous-session).

Pendant que les audits sont toujours en cours, le compteur de préparation affiche une barre de progression avec un statut court en dessous, qui indique l’étape en cours. Une fois les audits terminés, le compteur affiche le pourcentage de préparation final et le nombre d’opportunités.

## Catégories d’audit

Le contrôle en amont regroupe les audits associés dans des catégories, telles que **SEO** et **Accessibilité**. Chaque catégorie s’affiche sous la forme d’une carte qui indique le nombre d’opportunités trouvées ou indique que tous ses audits ont réussi sans opportunité.

Développez une catégorie pour afficher ses audits individuels. Chaque audit indique s’il a réussi ou trouvé des opportunités, une brève description et un nombre d’opportunités trouvées. Sélectionnez un audit qui a trouvé des opportunités d’ouvrir sa page de détails.

Pour obtenir la liste complète des catégories d&#39;audit et les audits de chacune d&#39;elles, voir [Catégories d&#39;audit de contrôle en amont](./overview.md#preflight-audit-categories).

## Détails de l’opportunité

La page des détails affiche les opportunités trouvées par l’audit sélectionné. Lorsque le même problème se produit à plusieurs endroits, chaque occurrence est appelée instance . Utilisez le navigateur (**Instance précédente** et **Instance suivante**) pour les parcourir. Il indique votre position, par exemple *1 des 5 instances trouvées*. Pour revenir au tableau de bord de préparation, sélectionnez la flèche vers l’arrière à côté du titre de l’audit ; le tableau de bord s’ouvre à nouveau et la catégorie de l’audit est développée.

![Page de détail d’un audit, présentant une opportunité et sa suggestion](./assets/audit-results/audit-detail.png){align="center"}

Chaque opportunité comprend :

* Badge de gravité ou d’impact indiquant l’importance de l’opportunité.
* Détails sur l’opportunité, tels qu’une description du problème, une recommandation et, pour l’accessibilité, la règle WCAG associée et le niveau de conformité.
* Une section **Élément** qui identifie l’élément affecté sur la page, avec un bouton **Mettre en surbrillance sur la page**. Lorsque l’élément comporte du texte lisible, la section est intitulée **Élément : Texte** et affiche ce texte ; dans le cas contraire, elle est intitulée **Élément : Sélecteur** et affiche le sélecteur CSS de l’élément. Pour les opportunités **Liens** et **Canoniques**, une section **URL actuelle** affiche également l’URL impliquée, que vous pouvez si possible ouvrir dans un nouvel onglet.
* Une section **Suggestion** avec un correctif recommandé. Lorsque la suggestion est générée par l’IA, elle est marquée comme étant générée par l’IA et peut inclure une brève justification expliquant la correction suggérée.

## Surligner sur la page

Une fois les audits terminés, vous pouvez rapidement localiser et comprendre une opportunité en la mettant en surbrillance directement sur la page.

Le contrôle en amont met en surbrillance l’élément concerné dans son contexte et connecte le résultat du panneau à l’emplacement exact dans votre contenu. Il est ainsi plus facile de vérifier et de résoudre les opportunités sans effectuer de recherche manuelle dans la page.

1. Ouvrez le panneau Contrôle en amont dans le contexte de la page à contrôler, puis sélectionnez **Analyser la page** pour exécuter les contrôles.
1. Sélectionnez un audit dans le tableau de bord de préparation, puis sélectionnez une opportunité à examiner.
1. Sélectionnez **Mettre en surbrillance sur la page**. L’aperçu fait automatiquement défiler la page jusqu’à la zone appropriée et met en surbrillance l’élément correspondant, afin que vous puissiez facilement identifier et optimiser l’opportunité en contexte.

La mise en surbrillance n’est pas possible pour chaque opportunité. Par exemple, lorsqu’une opportunité n’est pas liée à un élément spécifique, l’élément est masqué ou il ne se trouve plus sur la page. Dans ce cas, le bouton **Mettre en surbrillance sur la page** est grisé ; passez la souris dessus pour voir pourquoi.

Dans l’éditeur universel, la mise en surbrillance n’est pas encore prise en charge pour les opportunités **accessibilité** ; le bouton **Mettre en surbrillance sur la page** est grisé et vous pouvez le survoler pour en connaître la raison.

Dans l’éditeur universel, le contrôle en amont ne peut que mettre en surbrillance le contenu modifiable. Si l’élément concerné ne fait pas partie du contenu modifiable, le bouton **Mettre en surbrillance sur la page** est grisé ; passez la souris dessus pour voir pourquoi. Si l’élément lui-même n’est pas directement modifiable, mais que le bloc modifiable le plus proche l’est, le contrôle en amont met en surbrillance ce bloc et ajoute une note expliquant pourquoi.

Dans l’éditeur de page d’AEM Sites et Adobe Managed Services (AMS), la mise en surbrillance nécessite également le **mode d’édition**. Dans le **mode Aperçu**, le contrôle en amont affiche un **mise en surbrillance des problèmes non disponibles** notez-le ; passez en **mode d’édition** pour mettre en surbrillance les éléments de la page.

## Identifiant du traitement

Chaque exécution de contrôle en amont possède un identifiant de tâche unique, affiché au bas du panneau. Elle s’avère principalement utile lorsqu’un administrateur résout un problème d’exécution spécifique. Pointez sur l’ID et sélectionnez l’icône Copier qui s’affiche à droite ; l’ID est copié dans le presse-papiers et un message de confirmation s’affiche. Incluez cet identifiant lorsque vous signalez un problème.

Lorsque vous utilisez le contrôle en amont en dehors de l’éditeur universel (par exemple, via le Sidekick ou un signet), le pied de page du panneau affiche également le nom de votre organisation au-dessus de l’ID de tâche. Dans l’éditeur universel, votre organisation s’affiche dans l’en-tête AEM à la place.
