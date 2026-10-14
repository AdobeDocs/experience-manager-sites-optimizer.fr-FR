---
title: Contrôle en amont de Lorem Ipsum
description: Découvrez l’audit Lorem ipsum dans la section Contrôle en amont pour AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 587aec4eb905a2b1ced746590ca25b8ed97b16c1
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 1%
---
# audit de Lorem ipsum

L’audit **Lorem ipsum** détecte le texte d’espace réservé qui a été laissé dans le contenu de votre page.

## Pourquoi est-ce important ?

La publication d’une page avec un texte d’espace réservé la fait paraître inachevée pour les lecteurs. Les moteurs de recherche peuvent indexer le texte de l’espace réservé et l’afficher dans les résultats de recherche, et les plateformes sociales peuvent l’afficher dans les aperçus de liens. Le texte d’espace réservé est souvent masqué, par exemple dans le texte secondaire de l’image ou les libellés d’accessibilité. Si c’est le cas, les personnes qui utilisent des lecteurs d’écran ou d’autres technologies d’assistance peuvent encore l’entendre, même si elle n’apparaît pas sur la page.

## Ce que l’audit vérifie

L’audit signale chaque emplacement de la page où apparaît le texte d’espace réservé. Il vérifie le texte visible de la page, ainsi que plusieurs endroits où il peut ne pas être visible immédiatement ou du tout :

* texte de remplacement de l’image
* libellés et descriptions d’accessibilité
* espaces réservés des champs de formulaire
* infobulles
* titre de la page
* métadonnées, telles que la méta-description et les balises de partage sur les réseaux sociaux

Le code qui n’est pas présenté aux utilisateurs, tel que les scripts et les styles, n’est pas coché.

## Correspondance du texte

L&#39;audit recherche l&#39;expression « lorem ipsum » dans toute combinaison de lettres majuscules et minuscules. Il trouve également l’expression lorsque les mots sont fractionnés sur des lignes ou des éléments, ou qu’ils ne sont séparés par aucun espace. Si l’expression apparaît plusieurs fois dans le même élément ou attribut, cet emplacement est signalé une fois.

## Limites connues

* **Uniquement « lorem ipsum » :** aucun autre texte d’espace réservé, tel que « TBD » ou autres mots de remplissage latins sans « lorem ipsum », n’est détecté.
* **Mettre en surbrillance sur la page :** n’est pas disponible pour le titre de la page ou les métadonnées, car ils n’apparaissent pas sur la page. Utilisez le texte affiché dans l’opportunité pour les trouver.

## Comment résoudre

Lorsque l’audit détecte des opportunités, chacune d’elles identifie l’endroit où apparaît le texte d’espace réservé. Le cas échéant, utilisez **Mettre en surbrillance sur la page** pour accéder au texte de votre contenu. Remplacez l’espace réservé par du contenu réel ou supprimez-le. Pour le texte secondaire et les libellés d’accessibilité, écrivez une description de l’image ou du contrôle. Pour savoir comment examiner et résoudre les opportunités, voir [Résultats d’audit dans le contrôle en amont](../../audit-results.md).
