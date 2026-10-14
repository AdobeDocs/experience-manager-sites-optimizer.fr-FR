---
title: Contrôle canonique en amont
description: Découvrez l’audit canonique dans Contrôle en amont pour AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 5c97431c2029e117339877219c2d6e4e30902a70
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%
---
# Audit canonique

L’audit **canonique** examine le lien canonique sur votre page. Le lien canonique est une balise `<link rel="canonical">` dans le `<head>` de la page qui nomme l’URL préférée pour le contenu de la page. L’audit signale les liens canoniques manquants, incorrectement configurés ou qui pointent ailleurs que sur la page elle-même.

## Pourquoi est-ce important ?

Un même contenu est souvent accessible à plusieurs URL, avec ou sans barre oblique de fin, avec des paramètres de tracking, ou avec des majuscules ou des minuscules différentes. Les moteurs de recherche traitent chaque URL comme une page distincte, sauf indication contraire. Le lien canonique lui indique l’URL que vous préférez ; il peut ainsi regrouper les doublons, combiner des signaux de classement tels que des liens entrants sur une seule URL et afficher cette URL dans les résultats de recherche.

Un lien canonique qui est faux peut être pire que rien du tout. Les moteurs de recherche peuvent ignorer un lien canonique auquel ils ne peuvent pas faire confiance, par exemple un lien sans URL, un lien placé en dehors du `<head>` ou l’une des balises avec lesquelles ils ne sont pas d’accord. Un lien canonique pointant vers une autre page demande aux moteurs de recherche d’afficher cette page à la place de la vôtre, ce qui peut exclure votre page des résultats de recherche.

## Ce que l’audit vérifie

L&#39;audit recherche des problèmes dans trois domaines :

* **Si la page comporte un lien canonique :** le lien canonique est manquant ou la page en comporte plusieurs. Plusieurs liens canoniques pointant vers des URL différentes sont signalés séparément, car les moteurs de recherche peuvent tous les ignorer.
* **Si la balise est configurée correctement :** la balise est en dehors du `<head>`, n’a pas d’attribut `href` ou est vide, ou porte un attribut tel que `hreflang`, `media` ou `type` qui peut entraîner son ignorance par les moteurs de recherche.
* **Si l’URL est correcte :** l’URL canonique est relative et non absolue, contient des lettres majuscules dans le chemin d’accès ou la chaîne de requête, utilise un protocole différent (`http://` ou `https://`) de la page ou pointe vers une autre page que celle que vous modifiez.

## Comparaison de l’URL canonique

Le contrôle en amont s’exécute sur les pages d’aperçu, dont l’hôte est généralement différent de votre site de production. Pour éviter de marquer chaque page d’aperçu, l’audit ne compare pas l’hôte de l’URL canonique à l’hôte de la page. Lorsqu’il vérifie si le lien canonique pointe vers la page elle-même, il compare uniquement le chemin de l’URL, de sorte `https://www.example.com/products/shoes` correspond au `/products/shoes` de la page d’aperçu. Une barre oblique et une casse dans le chemin ne sont pas prises en compte comme différences pour ce contrôle.

## Limites connues

* **Domaine différent :** une URL canonique qui pointe vers un autre site n’est pas marquée par le contrôle en amont, car les hôtes de prévisualisation diffèrent toujours du site de production. Vérifiez que le domaine de l’URL canonique est celui attendu.
* **En-tête de `Link` HTTP :** le contrôle en amont vérifie uniquement la balise canonique, et non l’en-tête de `Link` HTTP. Une page qui définit son URL canonique uniquement dans l’en-tête est signalée comme dépourvue du lien canonique.

## Comment résoudre

Lorsque l&#39;audit trouve des opportunités, chacune d&#39;elles décrit le problème et le changement recommandé. Dans la plupart des cas, la page doit comporter exactement un lien canonique, dans l’`<head>` , avec une URL absolue avec un chemin d’accès en minuscules qui pointe vers la page elle-même. Si la page pointe intentionnellement vers une autre page en tant que version canonique, par exemple un doublon ou une copie pour imprimante, vous pouvez la laisser telle quelle. L&#39;audit le signalera quand même. Pour savoir comment examiner et résoudre les opportunités, voir [Résultats d’audit dans le contrôle en amont](../../audit-results.md).
