---
title: Résultats de l’audit dans le contrôle en amont
description: Découvrez comment interpréter les résultats de l’audit de contrôle en amont, la mesure des résultats et les catégories d’audit, et accédez aux opportunités dans l’aperçu.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 59c097682899889aa2a5d76333f80cc58e28ff1e
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 2%
---

# Résultats de l’audit dans le contrôle en amont

Une fois les audits terminés, le contrôle en amont affiche les résultats dans le tableau de bord de résultats. Le tableau de bord présente un indicateur de résultats global et les opportunités qu’il a détectées, regroupées par catégorie d’audit. Au sein de chaque catégorie, les audits individuels identifient des éléments spécifiques à examiner ou à corriger.

## Barre d’outils

La barre d’outils située en haut du tableau de bord des résultats fournit des actions pour l’exécution en cours :

* **Réanalyser** - Lancez une toute nouvelle exécution d’audit sur la page active. L’option Réanalyser ignore toujours les résultats affichés et exécute à nouveau chaque audit. Vous devez donc l’utiliser chaque fois que vous souhaitez de nouveaux résultats, par exemple, après avoir modifié la page. Sélectionnez **Réanalyser** dans la barre d’outils.
* **Exporter** - Téléchargez l’exécution actuelle au format **CSV** (feuille de calcul conviviale) ou **PDF** (document formaté). En fonction de votre environnement, sélectionnez **Exporter** dans la barre d’outils ou dans l’**Autres actions** (**...**) menu.
* **Paramètres** - Utilisez **Afficher les liens de navigation du site** pour inclure des liens de navigation du site (actuellement Liens internes uniquement). Sélectionnez l’icône d’engrenage ou ouvrez **Autres actions** (**...**). et sélectionnez **Paramètres**. Les paramètres sont disponibles avant une exécution ou une fois celle-ci terminée, mais pas pendant que les audits sont en cours d’exécution ni dans l’éditeur universel. Voir [Inclure des liens de navigation de site](./opportunities/seo/internal-links.md#include-site-navigation-links).

Si vous modifiez un paramètre après une exécution, un point sur **Réanalyser** et le libellé **Réanalyser pour appliquer de nouveaux paramètres** indiquent que les résultats affichés utilisaient un paramètre différent. Sélectionnez **Réanalyser** pour appliquer le paramètre enregistré à une nouvelle exécution.

Lors de l’exportation, vous pouvez également choisir les éléments à inclure :

* **Inclure le tableau des métadonnées** - Ajoutez un tableau des détails d’exécution, tels que les détails de l’hôte, du chemin de contenu et de la génération.
* **Inclure les audits réussis** - Inclure les audits réussis sans opportunités, pas seulement les opportunités trouvées.

>[!NOTE]
>
>Les exportations PDF sont toujours générées en anglais, quelle que soit la langue de l’interface. Les exportations de fichiers CSV suivent votre langue d’interface aussi étroitement que possible.

## Outil de mesure des résultats

En haut du tableau de bord, la mesure des résultats reflète les résultats d’audit globaux. Il indique le pourcentage d’audits qui se sont terminés sans opportunités, étiquetés **% réussis** ainsi que le nombre total d’opportunités trouvées dans tous les audits. Par exemple, le taux de réussite de **85 %** signifie que 85 % des vérifications terminées n&#39;ont trouvé aucune occasion. Ce pourcentage décrit les résultats de l’audit, et non la progression de l’exécution.

![Mesure des résultats et catégories d’audit dans le tableau de bord Contrôle en amont](./assets/overview/hero.png){align="center"}

Lorsque vous affichez une exécution qui a été rechargée à partir d’une session précédente, l’en-tête indique la durée de son exécution (par exemple, *hier*. Pour plus d’informations, voir [Poursuivre une session précédente](./audits.md#continue-a-previous-session).

Pendant que les audits sont toujours en cours d’exécution, le tableau de bord affiche **Page d’analyse** avec un statut court en dessous. Une barre de progression s’affiche initialement, avant l’arrivée des catégories d’audit nommées. Ensuite, un indicateur de traitement s’affiche uniquement à côté de chaque audit toujours en cours d’exécution, et non dans sa catégorie. Une fois tous les audits terminés, le compteur affiche le pourcentage final de réussite et le nombre d’opportunités.

## Catégories d’audit

Le contrôle en amont regroupe les audits associés dans des catégories, telles que **SEO** et **Accessibilité**. Chaque catégorie s’affiche sous la forme d’une carte qui indique le nombre d’opportunités trouvées ou indique que tous ses audits ont réussi sans opportunité.

Développez une catégorie pour afficher ses audits individuels. Chaque audit indique s’il a réussi ou trouvé des opportunités, une brève description et un nombre d’opportunités trouvées. Sélectionnez un audit qui a trouvé des opportunités d’ouvrir sa page de détails.

Une catégorie peut afficher des résultats alors que certains de ses audits sont toujours en cours. Son statut indique, par exemple, que les audits **3/3 ont été réalisés jusqu&#39;à présent**. Ce nombre inclut uniquement les audits qui ont renvoyé des résultats. Il peut donc changer à mesure que d’autres résultats arrivent. Développez la catégorie pour voir quels audits sont toujours en cours. Une catégorie sans opportunités n’affiche sa coche entièrement effacée qu’une fois son travail en attente terminé.

Pour obtenir la liste complète des catégories d&#39;audit et les audits de chacune d&#39;elles, voir [Catégories d&#39;audit de contrôle en amont](./overview.md#preflight-audit-categories).

## Détails de l’opportunité

La page des détails affiche les opportunités trouvées par l’audit sélectionné. Lorsque le même problème se produit à plusieurs endroits, chaque occurrence est appelée instance . Utilisez le navigateur (**Instance précédente** et **Instance suivante**) pour les parcourir. Il indique votre position, par exemple *1 des 5 instances trouvées*. Pour revenir au tableau de bord des résultats, sélectionnez la flèche vers l’arrière à côté du titre de l’audit ; le tableau de bord s’ouvre à nouveau et la catégorie de l’audit est développée.

Pour les audits qui identifient une URL spécifique sur la page, la section **Élément** s’affiche en haut de la carte pour présenter l’élément, et le reste de l’opportunité la suit dans sa propre section.

Lorsque plusieurs opportunités affectent le même élément (par exemple, plusieurs problèmes avec le même lien), le contrôle en amont les affiche ensemble sur une carte, chacune dans sa propre section intitulée avec son numéro d’instance, tel que **Instance 3**. Le navigateur affiche ensuite une plage au lieu d’une seule position, par exemple *3-5 sur 12 instances trouvées*.

![Page de détails de l’audit des liens internes, affichant le filtre d’instance, une opportunité et la section URL actuelle](./assets/audit-results/audit-detail.png){align="center"}

Chaque opportunité comprend :

* Détails sur l’opportunité, tels qu’une description du problème, une recommandation et, pour l’accessibilité, la règle WCAG associée et le niveau de conformité.
* Une section **Élément** qui identifie l’élément affecté sur la page, avec un bouton **Mettre en surbrillance sur la page**. Lorsque l’élément comporte du texte lisible, la section est intitulée **Élément : Texte** et affiche ce texte ; dans le cas contraire, elle est intitulée **Élément : Sélecteur** et affiche le sélecteur CSS de l’élément. Pour les opportunités **Liens internes** et **Canonique**, une section **URL actuelle** affiche également l’URL impliquée. Sélectionnez **Copier l’URL** pour la copier dans le presse-papiers, ou **Ouvrir dans un nouvel onglet** pour l’ouvrir.
* Une section **Suggestion** avec un correctif recommandé. Lorsque la suggestion est générée par l’IA, elle est marquée comme étant générée par l’IA et peut inclure une brève justification expliquant la correction suggérée.

### Filtrer les instances

Certains audits fournissent un filtre qui concentre la page de détails sur les instances que vous souhaitez examiner. Lorsqu’un audit en fournit un, une icône de filtre s’affiche en regard de l’en-tête **Instances**. Sélectionnez l’icône, puis choisissez une option. La page de chaque audit décrit ses options de filtrage.

Lorsque vous sélectionnez une option autre que la valeur par défaut, son nom apparaît en regard de l’icône de filtre et le navigateur ne parcourt que les instances correspondantes. Si aucune ne correspond, le contrôle en amont affiche **Aucune instance ne correspond à ce filtre.** Lorsqu’une carte affiche plusieurs opportunités pour le même élément, le filtre peut en masquer certaines.

Le filtre ne modifie pas le nombre d’opportunités dans le tableau de bord des résultats ou le rapport exporté.

## Surligner sur la page

Une fois les audits terminés, vous pouvez rapidement localiser et comprendre une opportunité en la mettant en surbrillance directement sur la page.

Le contrôle en amont met en surbrillance l’élément concerné dans son contexte et connecte le résultat du panneau à l’emplacement exact dans votre contenu. Il est ainsi plus facile de vérifier et de résoudre les opportunités sans effectuer de recherche manuelle dans la page.

1. Ouvrez le panneau Contrôle en amont dans le contexte de la page à contrôler, puis sélectionnez **Analyser la page** pour exécuter les contrôles.
1. Sélectionnez un audit dans le tableau de bord des résultats, puis sélectionnez une opportunité à examiner.
1. Sélectionnez **Mettre en surbrillance sur la page**. L’aperçu fait automatiquement défiler la page jusqu’à la zone appropriée et met en surbrillance l’élément correspondant, afin que vous puissiez facilement identifier et optimiser l’opportunité en contexte.

La mise en surbrillance n’est pas possible pour chaque opportunité. Par exemple, lorsqu’une opportunité n’est pas liée à un élément spécifique, l’élément est masqué ou il ne se trouve plus sur la page. Dans ce cas, le bouton **Mettre en surbrillance sur la page** est grisé ; passez la souris dessus pour voir pourquoi.

Dans l’éditeur universel, la mise en surbrillance n’est pas encore prise en charge pour les opportunités **accessibilité** ; le bouton **Mettre en surbrillance sur la page** est grisé et vous pouvez le survoler pour en connaître la raison.

Dans l’éditeur universel, le contrôle en amont ne peut que mettre en surbrillance le contenu modifiable. Si l’élément concerné ne fait pas partie du contenu modifiable, le bouton **Mettre en surbrillance sur la page** est grisé ; passez la souris dessus pour voir pourquoi. Si l’élément lui-même n’est pas directement modifiable, mais que le bloc modifiable le plus proche l’est, le contrôle en amont met en surbrillance ce bloc et ajoute une note expliquant pourquoi.

Dans l’éditeur de page d’AEM Sites et Adobe Managed Services (AMS), la mise en surbrillance nécessite également le **mode d’édition**. Dans le **mode Aperçu**, le contrôle en amont affiche un **mise en surbrillance des problèmes non disponibles** notez-le ; passez en **mode d’édition** pour mettre en surbrillance les éléments de la page.

## Identifiant du traitement

Chaque exécution de contrôle en amont possède un identifiant de tâche unique, affiché au bas du panneau. Elle s’avère principalement utile lorsqu’un administrateur résout un problème d’exécution spécifique. Pointez sur l’ID et sélectionnez l’icône Copier qui s’affiche à droite ; l’ID est copié dans le presse-papiers et un message de confirmation s’affiche. Incluez cet identifiant lorsque vous signalez un problème.

Lorsque vous utilisez le contrôle en amont en dehors de l’éditeur universel (par exemple, via le Sidekick ou un signet), le pied de page du panneau affiche également le nom de votre organisation au-dessus de l’ID de tâche. Dans l’éditeur universel, votre organisation s’affiche dans l’en-tête AEM à la place.
