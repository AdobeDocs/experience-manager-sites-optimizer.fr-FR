---
title: Contrôle en amont de l’audit des métadonnées
description: Découvrez l’audit des balises de métadonnées dans la section Contrôle en amont pour AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 59c097682899889aa2a5d76333f80cc58e28ff1e
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 1%
---
# Audit des métadonnées

L’audit **Metatags** examine le titre de la page, la méta-description et l’en-tête principal (H1). Il signale toutes les pages qui sont manquantes, vides ou en dehors de la longueur recommandée et signale les pages comportant plusieurs en-têtes H1.

## Pourquoi est-ce important ?

Le titre et la méta-description de la page sont généralement ceux que les utilisateurs voient pour votre page dans les résultats de recherche : le titre comme titre cliquable et la description comme résumé en dessous. Un titre ou une description manquants ou de mauvaise taille peuvent être tronqués ou remplacés par du texte sélectionné par le moteur de recherche sur votre page. L’en-tête H1 indique aux lecteurs et aux moteurs de recherche l’objet principal de la page. Par conséquent, une page doit avoir un H1 clair.

## Ce que l’audit vérifie

L&#39;audit signale une opportunité pour chacun des problèmes suivants :

* **Titre de la page :** manquant, vide, trop court ou plus long que la longueur idéale.
* **Description Meta :** manquant, vide, trop court ou plus long que la longueur idéale.
* En-tête **H1 :** manquant, vide, plus long que la longueur idéale ou plus d’un H1 sur la page.

Une valeur de quelques caractères au-dessus de la longueur idéale est signalée comme **supérieure à la longueur idéale**, et une valeur supérieure au maximum de l’audit comme **trop longue**. Le contrôle en amont ne comporte pas de seuil trop long pour les titres de page.

| Balise | Longueur idéale | Au-dessus de la longueur idéale | Trop long |
|---|---|---|---|
| Titre de la page | 40 à 60 caractères | Plus de 60 caractères | - |
| Description du Meta | 140 à 160 caractères | 161 à 175 caractères | Plus de 175 caractères |
| En-tête H1 | Jusqu’à 70 caractères | 71 à 75 caractères | Plus de 75 caractères |

Ces plages sont des directives recommandées et non des exigences pour les moteurs de recherche. Le contrôle en amont les utilise pour décider quand signaler une opportunité.

## Lecture des valeurs

L’audit lit la page que vous modifiez : le texte de l’élément `<title>`, le contenu de la balise `<meta name="description">` et le texte visible du premier élément `<h1>`, y compris le texte en gras ou en italique.

Une balise est **manquante** quand la page ne l’a pas, et **vide** quand elle y est mais sans texte visible. Les longueurs comptent tous les caractères, y compris les espaces et la ponctuation. Seule la longueur H1 est vérifiée. Lorsqu’une page comporte plusieurs H1, chacune d’elles est répertoriée comme une instance distincte. Vous pouvez ainsi rechercher et modifier les en-têtes supplémentaires.

## Suggestions

Chaque opportunité inclut une recommandation, telle que la longueur idéale pour la balise ou un H1 sur une page.

Le titre de la page, la méta-description et les opportunités H1 peuvent également inclure une suggestion générée par l’IA, écrite à partir du propre contenu de votre page. Une suggestion n’est affichée que si elle correspond à la longueur idéale. Examinez et modifiez chaque suggestion avant de l’utiliser.

Lorsqu’une opportunité H1 n’a pas de suggestion d’IA, sa suggestion est un conseil fixe à la place, comme raccourcir le titre ou remplacer les titres H1 supplémentaires par H2. Lorsqu’un titre de page ou une opportunité de méta-description ne comporte aucune suggestion d’IA, le contrôle en amont indique qu’aucune suggestion n’est disponible.

## Si une valeur avec indicateur vous semble correcte

Dans les pages Edge Delivery Services, un titre de page ou une méta-description que vous n’avez pas défini est rempli automatiquement à partir du premier en-tête et du premier paragraphe de la page. Elles sont souvent plus courtes que la longueur idéale, de sorte que la page est marquée. Définir votre propre titre et votre propre description dans les métadonnées de page résout ce problème.

## Limites connues

* **Les autres balises head ne sont pas cochées** telles que les balises Open Graph pour le partage sur les réseaux sociaux ou la balise robots.
* **La longueur est comptée en caractères :** les moteurs de recherche raccourcissent les titres et les descriptions en fonction de l’espace qu’ils occupent à l’écran, de sorte qu’une valeur de la longueur idéale peut toujours être raccourcie dans les résultats de recherche.
* **Langues sans espaces entre les mots :** sur les pages dans des langues telles que le chinois, le japonais ou le coréen, une valeur qui lit bien peut toujours être marquée et les suggestions de l’IA peuvent ne pas correspondre à la longueur idéale.

## Comment résoudre

Chaque opportunité décrit le problème et la modification recommandée, et affiche la valeur actuelle du titre de la page ou de la méta-description.

* **Titre de la page et méta-description :** mettez-les à jour là où votre site les définit, par exemple dans les propriétés de la page dans AEM Sites ou dans les métadonnées de la page dans Edge Delivery Services. Ces balises se trouvent dans l’en-tête de la page. Par conséquent, l’option **Mettre en surbrillance sur la page** n’est pas disponible pour elles.
* En-tête **H1 :** utilisez **Mettre en surbrillance sur la page** pour trouver l’en-tête dans votre contenu. Dans Edge Delivery Services, l’éditeur de page d’AEM Sites et Adobe Managed Services (AMS), le contrôle en amont fait défiler l’en-tête jusqu’à le mettre en surbrillance ; l’éditeur de page et AMS nécessitent le **mode d’édition**. Dans l’éditeur universel, le contrôle en amont sélectionne l’en-tête ou le bloc modifiable le plus proche qui le contient. Un en-tête dans la navigation ou un pied de page est affiché, mais ne peut pas être sélectionné. Pour plus d’informations, voir [Surligner sur la page](../../audit-results.md#highlight-on-page).

Pour savoir comment examiner et résoudre les opportunités, voir [Résultats d’audit dans le contrôle en amont](../../audit-results.md).
