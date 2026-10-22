---
title: Contrôle en amont de l’audit des liens externes
description: Découvrez l’audit des liens externes dans Contrôle en amont pour AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 13bc34bf4c3d31e730dbe597b84fd6d594df6fea
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%
---
# Audit des liens externes

L’audit **Liens externes** examine les liens de votre page qui pointent vers d’autres sites. L’audit vérifie chaque lien externe de la page que vous modifiez et signale ceux qui sont rompus, non sécurisés ou qui n’ont pas pu être vérifiés automatiquement.

## Pourquoi est-ce important ?

Un lien externe rompu est une impasse pour le lecteur et un signal aux moteurs de recherche que la page n&#39;est pas bien entretenue. Les liens externes sont également ceux sur lesquels vous avez le moins de contrôle : l’autre site peut déplacer, renommer ou supprimer une page à tout moment et votre lien cesse de fonctionner en silence. En les vérifiant avant de les publier, vous capturez les liens qui sont devenus obsolètes depuis leur ajout initial.

## Ce que l’audit vérifie

L’audit signale une opportunité pour chaque lien externe présentant l’un des problèmes suivants :

* **Lien rompu :** le lien renvoie `Status 404` ou `Status 410`, ou son site n’est pas accessible du tout, par exemple parce que le domaine n’existe plus. Un lien qui atteint l’erreur après une redirection est signalé de la même manière.
* **Lien non sécurisé :** le lien utilise `http://` et le site ne le redirige pas vers `https://`. Un lien qui commence par `http://` mais est redirigé vers une page `https://` sécurisée n’est pas marqué. Mettez à jour le lien pour utiliser `https://`.
* **Lien non vérifié :** le contrôle en amont n’a pas pu confirmer que le lien fonctionne, par exemple, car le site nécessite une connexion, bloque les vérifications automatisées, renvoie constamment une erreur de serveur, ne répond pas à temps ou redirige trop de fois. Certains réseaux sociaux, tels que LinkedIn et Instagram, signalent les pages qui existent comme manquantes aux contrôles automatisés, de sorte que les erreurs de pages manquantes de ces sites sont également signalées comme non vérifiées. Il est très probable que ces liens fonctionnent dans un navigateur. Par conséquent, le contrôle en amont ne les signale pas comme rompus. Au lieu de cela, il vous demande d’ouvrir le lien et de le confirmer vous-même, puis le signale avec un impact faible.

Un lien peut être à la fois non sécurisé et rompu, ou à la fois non sécurisé et non vérifié, auquel cas les deux opportunités sont signalées. Un lien qui est résolu avec succès n’est pas marqué, même s’il comporte des redirections en cours de route.

## Quels liens sont vérifiés

Chaque lien externe de la page est coché. Un lien externe est tout lien dont l’hôte diffère de la page que vous modifiez. L’hôte correspond au nom de domaine et à tout port non standard, tel que `:8443`. Les sous-domaines sont comptés comme des hôtes différents. Par conséquent, `blog.example.com` et `example.com` sont tous deux externes à `www.example.com`. Les liens vers le même hôte, y compris les liens `http://` vers votre propre site, sont couverts par l’audit [Liens internes](./internal-links.md) à la place. Les liens de navigation du site sont toujours inclus, car le paramètre **Afficher les liens de navigation du site** s’applique uniquement à l’audit des liens internes. Les liens tels que `mailto:`, `tel:` et `javascript:` sont ignorés.

Chaque lien est signalé une fois, même s’il apparaît plusieurs fois sur la page ou avec différentes ancres, telles que `#pricing` et `#features`. L’opportunité met en évidence la première place où apparaît le lien.

Les liens que le vérificateur de liens d’AEM a déjà marqués comme non valides sont inclus dans l’audit, même si l’éditeur supprime le lien cliquable de la page. Ils sont revérifiés plutôt que d’être approuvés, de sorte qu’un lien qui a commencé à fonctionner depuis n’est pas signalé.

## Limites connues

* **Adresses privées :** les liens vers des adresses réseau privées ou internes, telles qu’un site intranet, ne sont pas vérifiés et ne sont pas signalés.
* **Vue côté serveur :** le contrôle en amont vérifie les liens externes à partir des serveurs Adobe plutôt qu’à partir de votre navigateur. Un site qui se comporte différemment en fonction de l’emplacement, de la connexion ou de la détection des robots peut renvoyer un résultat différent de celui que vous voyez dans votre navigateur. Ces liens sont généralement signalés comme **Lien non vérifié** plutôt que comme rompus.

## Comment résoudre

Lorsque l&#39;audit trouve des opportunités, chacune d&#39;elles décrit le problème et le changement recommandé, et identifie le lien impliqué. Utilisez **Mettre en surbrillance sur la page** pour accéder au lien dans votre contenu, puis ouvrez l’URL dans un nouvel onglet pour confirmer le problème par vous-même. En cas de lien rompu, mettez-le à jour vers le nouvel emplacement de la page ou supprimez-le. Si le lien n’est pas vérifié, vérifiez qu’il s’ouvre correctement dans votre navigateur. Pour savoir comment examiner et résoudre les opportunités, voir [Résultats d’audit dans le contrôle en amont](../../audit-results.md).
