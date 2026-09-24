---
title: Contrôle en amont de l’audit de la taille du corps
description: Découvrez l’audit de la taille du corps dans Contrôle en amont pour AEM Sites Optimizer.
source-git-commit: c85cfb84b315b64ab5fcddfaa192ce78dd8d1a67
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%
---
# Audit de la taille du corps

L’audit **Taille du corps** examine la quantité de contenu du corps sur votre page. Les pages comportant très peu de contenu peuvent être moins utiles aux lecteurs et se classer mal dans les résultats de recherche. L’audit signale les pages qui semblent contenir trop peu de texte.

## Pourquoi est-ce important ?

Les moteurs de recherche et les assistants d’IA s’appuient sur le texte d’une page pour comprendre de quoi il s’agit. Une page avec peu ou pas de texte est souvent traitée comme une page de faible valeur, ce qui peut nuire à son classement et à son affichage dans les réponses de l’IA.

## Ce que l’audit vérifie

L’audit mesure la quantité de texte créé sur la page et signale deux situations :

* **Pas de contenu texte :** la page a été lue avec succès mais ne comporte aucun texte de corps, par exemple une page qui n’est qu’une image.
* **Contenu fluide :** la page comporte du texte, mais moins que le minimum recommandé.

Une page contenant suffisamment de texte passe sans être marquée.

## Comment votre contenu est mesuré

L’audit mesure le texte dans la zone de contenu principale de votre page, et non la page entière. Les éléments partagés tels que la navigation, les en-têtes, les pieds de page et les chemins de navigation se répètent sur chaque page et l’audit les exclut là où il peut les reconnaître afin que ce chrome partagé ne masque pas le contenu réellement fluide. La façon dont il peut séparer complètement votre contenu de ce chrome dépend du balisage de votre page, comme décrit ci-dessous.

Pour trouver votre contenu, l’audit utilise la première de ces options qui s’applique :

1. **`<main>`(ou `role="main"`).** Cette zone est traitée comme la zone de contenu définitive, et seul le texte qu’elle contient est mesuré (si une page comporte plusieurs éléments de ce type, leur texte est combiné). Il s’agit de l’option la plus fiable.
1. **Corps de la page, avec suppression de Chrome.** S’il n’existe aucune `<main>` ni aucun `role="main"`, l’audit mesure le `<body>` après la suppression du Chrome de page reconnu : navigation et en-tête et pied de page, qu’ils soient marqués avec des balises HTML standard, des rôles repères ARIA ou les composants standard d’en-tête, de pied de page, de chemin de navigation et de chemin de navigation d’AEM. Un en-tête ou un pied de page appartenant à une section de contenu, tel que le titre ou la signature d’un article, est conservé.
1. **L’ensemble du corps de la page.** S’il n’existe aucun point de repère de contenu ni aucun chrome reconnu, l’`<body>` entière est mesurée.

Quelques remarques sur ce qui compte. Les images ne fournissent aucun texte (leur texte `alt` n’est pas mesuré). Il est donc possible d’ajouter un indicateur à une page qui est principalement constituée d’images. Le texte à l’intérieur des balises `<script>` et `<style>` n’est jamais comptabilisé, de sorte que les scripts d’analyse ou de couche de données ne gonflent pas la mesure. Le texte de lien ordinaire, cependant, est comptabilisé comme tout autre texte de votre contenu.

## Si une page avec indicateur vous semble correcte

Si une page est marquée comme mince mais que vous êtes sûr qu’elle contient suffisamment de contenu, l’audit peut ne pas avoir séparé clairement votre contenu de la Chrome qui l’entoure, tel que la navigation, les en-têtes et les pieds de page.

Si vous souhaitez que l’audit mesure plus précisément votre page, les choix de balisage suivants peuvent l’aider :

* L’option la plus fiable consiste à encapsuler le contenu créé dans un élément de `<main>` (ou à ajouter des `role="main"`). Cela supprime toute ambiguïté, de sorte que seul votre contenu est mesuré.
* Si vous ne pouvez pas ajouter de `<main>`, les balises d’en-tête et de pied de page standard (`<header>`, `<footer>`) ou les variations de fragment d’expérience d’en-tête et de pied de page standard d’AEM aident l’audit à reconnaître et à exclure votre chrome de page.
* Le marquage des en-têtes et des pieds de page au niveau de la section dans `<article>`, `<section>` ou `<aside>` empêche le dépôt du contenu qui réside dans ces en-têtes et pieds de page.

## Limites connues

L’audit s’appuie sur le balisage de votre page pour distinguer le contenu de Chrome. Sur une page qui ne comporte **aucun `<main>`, aucun balisage de repère standard et composants d’en-tête/de pied de page nommés différemment des conventions de la plateforme**, un texte chromé peut être inclus dans la mesure ou du texte créé peut parfois être exclu. L’ajout d’un élément de `<main>` autour de votre contenu résout tous ces cas. L’audit ne tente pas de deviner la zone de contenu à partir de la densité du texte ou de la mise en page visuelle ; il s’appuie sur des signaux de balisage afin que les résultats soient prévisibles et répétables.

## Comment résoudre

Lorsque l&#39;audit trouve des opportunités, chacune d&#39;elles décrit le problème et le changement recommandé. Pour savoir comment examiner et résoudre les opportunités, voir [Résultats d’audit dans le contrôle en amont](../../audit-results.md).
