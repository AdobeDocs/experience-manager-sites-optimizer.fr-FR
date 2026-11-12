---
title: Contrôle en amont de l’audit des liens externes
description: Découvrez l’audit des liens externes dans Contrôle en amont pour AEM Sites Optimizer.
badgePreflightSEO: label="Contrôle en amont - SEO" type="Caution" url="../seo.md" tooltip="Contrôle en amont - SEO"
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 659419fa2eb570b4e1fedf87c35c5c60c46ffc8a
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 0%
---
# Contrôle en amont - Audit des liens externes

L’audit **Liens externes** examine les liens de votre page qui pointent vers d’autres sites. L’audit vérifie chaque lien externe de la page que vous modifiez et signale ceux qui sont rompus, non sécurisés ou qui n’ont pas pu être vérifiés automatiquement.

## Pourquoi est-ce important ?

Un lien externe rompu est une impasse pour le lecteur et un signal aux moteurs de recherche que la page n&#39;est pas bien entretenue. Les liens externes sont également ceux sur lesquels vous avez le moins de contrôle : l’autre site peut déplacer, renommer ou supprimer une page à tout moment et votre lien cesse de fonctionner en silence. En les vérifiant avant de les publier, vous capturez les liens qui sont devenus obsolètes depuis leur ajout initial.

## Ce que l’audit vérifie

L’audit trie les problèmes en trois groupes :

* **Rompu :** le lien échoue actuellement pour chaque visiteur et ne devrait pas être récupéré.
* **Non vérifié :** le lien échoue pour certains visiteurs, peut échouer seulement temporairement ou ne peut pas être vérifié.
* **Bonne pratique :** le lien fonctionne, mais il ne doit pas être créé de cette manière, comme un lien `http://` non sécurisé.

L’audit signale une opportunité pour chaque lien externe présentant l’un des problèmes suivants :

* **Lien rompu :** le lien ne fonctionne pour personne qui l&#39;ouvre. Le contrôle en amont signale qu’un lien est rompu lorsque :
  * son site n’est pas accessible du tout, par exemple parce que le domaine n’existe plus.
  * elle renvoie `Status 404` ou `Status 410`.
  * elle renvoie `Status 405`, ce qui signifie que le site rejette les requêtes de page normales.
  * il redirige en boucle ou plus de 20 fois. Les navigateurs utilisent la même limite et affichent une erreur « trop de redirections ».

  Un lien qui atteint l’une de ces erreurs après une redirection est signalé de la même manière.
* **Lien non sécurisé :** le lien utilise `http://` et le contrôle en amont ne l&#39;a pas vu rediriger vers `https://`, y compris lorsque le site n&#39;a pas répondu. Un lien commençant par `http://` mais redirigé vers une page `https://` sécurisée n’est pas marqué. Mettez à jour le lien pour utiliser `https://`.
* **Lien non vérifié :** Preflight n&#39;a pas pu confirmer si le lien fonctionne, il vous demande donc d&#39;ouvrir le lien et de le vérifier vous-même. L’opportunité explique quel cas s’applique :
  * **Nécessite une connexion :** le lien renvoie `Status 401`. Les visiteurs ne disposant pas d’un compte ne peuvent pas l’ouvrir. Vérifiez donc que cela est prévu.
  * **Bloque les vérifications automatisées :** le lien renvoie `Status 403` ou `Status 429`, ou le site bloque les demandes automatisées d’une autre manière, comme le fait LinkedIn. Vérifiez que le lien s’ouvre dans un navigateur.
  * **Les sites sociaux et les sites protégés par un mur de connexion :** LinkedIn, Instagram, Facebook, X (Twitter), TikTok et Threads renvoient des erreurs trompeuses aux requêtes anonymes. Par conséquent, une boucle de redirection `Status 404`, `Status 410`, `Status 405` ou de ces sites est signalée comme non vérifiée plutôt que comme rompue.
  * **Erreur de serveur :** le lien renvoie une erreur de serveur (`Status 5xx`) qui persiste lorsque le contrôle en amont le vérifie à nouveau. Le contrôle en amont effectue une nouvelle tentative avant de le signaler. L’erreur peut être temporaire. Vérifiez donc que le lien fonctionne avant de le publier.
  * **Indisponible pour des raisons juridiques :** le lien renvoie `Status 451` dans la région d&#39;où proviennent les contrôles en amont. Vérifiez que cela fonctionne pour votre audience.
  * **Aucune réponse à temps :** le site n&#39;a pas répondu à temps, même après une nouvelle tentative de contrôle en amont. Le site peut être lent ou temporairement inactif.

Un lien peut être à la fois non sécurisé et rompu, ou à la fois non sécurisé et non vérifié, auquel cas les deux opportunités sont signalées. Une chaîne de redirection seule n’est pas marquée si elle atteint une page de travail dans les 20 redirections.

## Quels liens sont vérifiés

Chaque lien externe de la page est coché. Un lien externe est tout lien dont l’hôte diffère de la page que vous modifiez. L’hôte est le nom de domaine plus tout port non standard, tel que `:8443`. Les sous-domaines sont comptés comme des hôtes différents. Par conséquent, `blog.example.com` et `example.com` sont tous deux externes à `www.example.com`. Les liens vers le même hôte, y compris les liens `http://` vers votre propre site, sont plutôt couverts par l’audit [Liens internes](./internal-links.md). Les liens de navigation du site sont toujours inclus, car le paramètre **Afficher les liens de navigation du site** s’applique uniquement à l’audit des liens internes. Les liens tels que `mailto:`, `tel:` et `javascript:` sont ignorés.

Chaque lien est signalé une fois, même s’il apparaît plusieurs fois sur la page ou avec des ancres différentes, telles que `#pricing` et `#features`. L’opportunité met en évidence la première place où apparaît le lien.

Les liens que le vérificateur de liens d’AEM a déjà marqués comme non valides sont inclus dans l’audit, même si l’éditeur supprime le lien cliquable de la page. Ils sont revérifiés plutôt que d’être approuvés, de sorte qu’un lien qui a commencé à fonctionner depuis n’est pas signalé.

## Filtrer les résultats

Sur la page de détails, utilisez le filtre en regard de l’en-tête **Instances** pour n’afficher que certaines des opportunités :

| Filtrer | Opportunités affichées |
|---|---|
| **Tous** (par défaut) | Chaque opportunité |
| **Cassé** | Liens rompus |
| **Vérification requise** | Liens non vérifiés et liens non sécurisés |

Si un lien comporte plusieurs opportunités, par exemple un lien non sécurisé qui est également rompu, chaque opportunité apparaît sous son propre filtre. Pour plus d’informations, voir [Filtrer les instances](../../audit-results.md#filter-instances).

## Limites connues

* **Adresses privées :** les liens vers des adresses réseau privées ou internes, telles qu&#39;un site intranet, ne sont pas vérifiés et ne sont pas signalés.
* **Limites de temps :** chaque lien possède sa propre limite de temps. Par conséquent, un site lent n&#39;empêche pas la vérification d&#39;autres liens. Chaque lien de la page obtient un résultat. Un lien qui ne répond pas à temps, même après une reprise, est signalé comme **Lien non vérifié** plutôt que rompu.
* **Domaines exclus :** la configuration de votre site peut exclure des domaines spécifiques de la vérification. Les liens vers un domaine exclu ou vers l’un de ses sous-domaines ne sont pas vérifiés et ne sont pas signalés.
* **Vue côté serveur :** le contrôle en amont vérifie les liens externes à partir des serveurs Adobe plutôt qu’à partir de votre navigateur. Un site qui se comporte différemment en fonction de l’emplacement, de la connexion ou de la détection des robots peut renvoyer un résultat différent de celui que vous voyez dans votre navigateur. Ces liens sont généralement signalés comme **Lien non vérifié** plutôt que comme rompu.

## Comment résoudre

Lorsque l&#39;audit trouve des opportunités, chacune d&#39;elles décrit le problème et le changement recommandé, et identifie le lien impliqué. Utilisez **Mettre en surbrillance sur la page** pour accéder au lien dans votre contenu et ouvrir l’URL dans un nouvel onglet pour confirmer le problème par vous-même. Agissez ensuite sur l’opportunité :

* **Lien rompu :** mettez à jour le lien vers le nouvel emplacement de la page, ou remplacez-le ou supprimez-le. Pour une boucle de redirection, contactez le propriétaire de l&#39;autre site ou le lien vers une autre source.
* **Lien non sécurisé :** modifiez le lien pour utiliser `https://`, après avoir confirmé que la version sécurisée fonctionne.
* **Lien non vérifié :** ouvrez le lien dans votre navigateur et vérifiez qu’il affiche la page attendue. Pour un lien qui nécessite une connexion, vérifiez que vos lecteurs doivent disposer d’un compte . En cas d’erreur de serveur, vérifiez à nouveau le lien avant de procéder à la publication. Si le lien ne fonctionne pas, traitez-le comme rompu.

Pour savoir comment examiner et résoudre les opportunités, consultez [Résultats d’audit dans le contrôle en amont](../../audit-results.md).
