---
title: Contrôle en amont de l’audit des liens internes
description: Découvrez l’audit des liens internes dans la section Contrôle en amont pour AEM Sites Optimizer.
source-git-commit: d87b607248efdeecf1ba29ede03bf1628d1dff30
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%
---
# Audit des liens internes

L’audit **Liens internes** examine les liens de votre page qui renvoient à votre propre site. L’audit vérifie chaque lien interne de la page que vous modifiez et signale ceux qui sont rompus, non sécurisés ou orientés vers un emplacement qu’un visiteur ne peut pas suivre.

## Pourquoi est-ce important ?

Un lien interne rompu est une impasse pour le lecteur et une explore perdue pour un moteur de recherche, qui ne transmet aucune valeur à la page qu’il était censé atteindre. Les liens internes sont également les plus faciles à rompre par accident : une page est déplacée ou renommée et chaque lien vers celle-ci cesse de fonctionner en silence. Comme les liens se trouvent tous sur votre propre site, ce sont également ceux que vous pouvez corriger vous-même.

## Ce que l’audit vérifie

L’audit signale une opportunité pour chaque lien interne présentant l’un des problèmes suivants :

* **Lien rompu :** le lien renvoie une erreur, telle que `Status 404` ou `Status 500`. Un lien qui atteint l’erreur après une redirection est signalé de la même manière.
* **Lien non sécurisé :** le lien utilise `http://` au lieu de `https://`. Lorsque la version sécurisée de la même URL fonctionne, le contrôle en amont l’offre comme suggestion.
* **URL de l’éditeur :** le lien pointe vers une URL d’éditeur AEM plutôt que vers la page de contenu. Le lien fonctionne pour vous lors de la création, ce qui le rend facile à manquer, mais chaque visiteur accède à l’interface de création. Le contrôle en amont suggère l’URL de contenu.
* **Fragment manquant :** le lien pointe vers une ancre, telle que `#pricing`, que la page cible ne contient pas. La page s’ouvre toujours, mais le lecteur ou la lectrice arrive en haut de la page au lieu de la section que vous vouliez dire. L’impact est donc inférieur à celui d’un lien rompu. Si la même ancre est mise en majuscules différemment dans la page, le contrôle en amont suggère l’ancre corrigée. Si la page cible elle-même est rompue, elle est signalée comme un **lien rompu** à la place.
* **Lien non vérifié :** la vérification a expiré ou a rencontré une erreur réseau. Le contrôle en amont ne peut pas déterminer si le lien fonctionne. Il vous demande donc de vérifier le lien vous-même plutôt que de le signaler comme rompu.

Un lien qui est résolu avec succès n’est pas marqué, même s’il comporte plusieurs redirections en cours de route. Il ne s’agit pas non plus d’un lien qui redirige vers un autre site, car il ne s’agit plus d’un lien interne.

## Comment les liens sont vérifiés

L’audit vérifie les liens de votre session de création afin qu’ils soient affichés tels que vous les avez connectés. Une page qui n’existe que sur l’instance de création est résolue correctement au lieu d’avoir l’air endommagée.

Les liens que le vérificateur de liens d’AEM a déjà marqués comme non valides sont inclus dans l’audit, même si l’éditeur supprime le lien cliquable de la page. Ils sont ensuite revérifiés au lieu d’être acceptés en confiance, de sorte qu’un lien qui a commencé à fonctionner depuis n’est pas signalé.

Une opportunité est signalée pour chaque emplacement où un lien s’affiche. Ainsi, un lien incorrect utilisé à trois endroits vous donne trois instances à corriger, chacune mettant en surbrillance sa propre place sur la page. Lorsque l’un de ces emplacements présente plusieurs problèmes, le contrôle en amont les présente ensemble sur une seule carte.

## Limites connues

L’audit s’exécute dans l’éditeur de page d’AEM Sites, dans Adobe Managed Services (AMS) et dans la création basée sur des documents via Sidekick. Il n’est actuellement pas disponible dans l’éditeur universel.

## Comment résoudre

Lorsque l&#39;audit trouve des opportunités, chacune d&#39;elles décrit le problème et le changement recommandé, et identifie le lien impliqué. Utilisez **Mettre en surbrillance sur la page** pour accéder au lien dans votre contenu, puis utilisez la section **URL actuelle** pour copier l’URL ou ouvrez-la dans un nouvel onglet afin de confirmer le problème pour vous-même. Pour savoir comment examiner et résoudre les opportunités, voir [Résultats d’audit dans le contrôle en amont](../../audit-results.md).
