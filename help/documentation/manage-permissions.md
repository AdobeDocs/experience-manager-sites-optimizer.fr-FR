---
title: Gérer les autorisations utilisateur
description: Découvrez comment gérer l’accès et les fonctionnalités des utilisateurs dans AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: c372679073253df686a77daccb6cb548622181f5
workflow-type: tm+mt
source-wordcount: '1362'
ht-degree: 1%
---
# Gestion des autorisations utilisateur

Contrôlez qui peut accéder à un site dans Sites Optimizer et ce qu’il peut en faire. Access est construit à partir d&#39;un petit ensemble de *fonctionnalités* indépendantes — Afficher, Modifier, Déployer, Configurer et Gérer les utilisateurs — que vous accordez à chaque personne.

L’accès est **additif** : les autorisations d’une personne représentent la somme de tout ce qui lui a été accordé. Il n&#39;y a pas de « refus », donc les subventions ne se contredisent jamais ou ne s&#39;annulent jamais. Pour accorder moins d’accès à quelqu’un, supprimez une autorisation plutôt que d’essayer de la remplacer.

Pour gérer l’accès, ouvrez l’onglet **Autorisations** (l’icône de cadenas dans le volet de navigation de gauche), puis sélectionnez le site à gérer.

![Page Autorisations dans Sites Optimizer](./assets/settings/permissions-page.png){align="center"}

## Accorder l’accès

Une personne peut y accéder de deux manières différentes, qui fonctionnent ensemble :

- **Accès à l’échelle de l’organisation** : attribué par l’administrateur de l’organisation Adobe dans le [Adobe Admin Console](https://adminconsole.adobe.com/). Elle s’applique à tous les sites de votre entreprise. Utilisez-le pour les personnes qui ont besoin du même accès partout.
- **Accès au niveau du site** : attribué dans Sites Optimizer, dans l’onglet **Autorisations**. Il s’applique à un seul site et peut être aussi large ou étroit que vous le souhaitez. Aucun accès Admin Console n’est requis.

>[!NOTE]
>
>Les deux calques s’additionnent. Une personne disposant d’un accès en affichage à l’échelle de l’organisation qui bénéficie également de la autorisation Modifier sur un site peut afficher chaque site et le modifier. Pour limiter une personne à un seul site, veillez à ce qu’elle ne détienne pas également un rôle à l’échelle de l’organisation.

### Rôles à l’échelle de l’organisation (Admin Console)

L’accès à l’échelle de l’organisation provient de l’un des deux **rôles de produit**, affectés dans le [Adobe Admin Console](https://adminconsole.adobe.com/) :

- **ASO Manager** — Accès complet à tous les sites, y compris **Gérer les utilisateurs**. Un responsable peut ouvrir l’onglet **Autorisations** pour n’importe quel site et attribuer l’accès à d’autres.
- **Utilisateur ASO** — accès en lecture seule à chaque site. Aucune modification et aucune gestion des utilisateurs.

Pour attribuer un rôle, vous devez être un **administrateur système** pour l’organisation ou un **administrateur de produit** pour AEM Sites Optimizer.

1. Connectez-vous à [](https://adminconsole.adobe.com/).
1. Accédez à **Produits** et sélectionnez **AEM Sites Optimizer**.
1. Ouvrez l’onglet **Utilisateurs** et ajoutez l’utilisateur par e-mail (ou sélectionnez un utilisateur existant).
1. Cliquez sur l’icône **+** (ajouter) pour ajouter un profil de produit, puis choisissez le profil de produit.

   ![Choix du profil de produit d’un utilisateur dans Adobe Admin Console](./assets/settings/permissions-admin-console-product-profile.png){align="center"}

1. Cliquez sur **Suivant**.
1. Choisissez le rôle **ASO Manager** pour un accès complet ou **ASO User** pour un accès en lecture seule, puis cliquez sur **Appliquer**.

   ![Sélection du rôle de responsable ASO dans le Adobe Admin Console](./assets/settings/permissions-admin-console-aso-manager-role.png){align="center"}

   ![Sélection du rôle Utilisateur ASO dans le Adobe Admin Console](./assets/settings/permissions-admin-console-aso-user-role.png){align="center"}

Pour plus d’informations sur l’ajout d’utilisateurs, voir [Intégration d’utilisateurs](setup/onboard-users.md).

>[!IMPORTANT]
>
>Seul un administrateur d’organisation peut octroyer des **Gérer les utilisateurs** à l’échelle de l’organisation. Un membre disposant de l’autorisation **Gérer les utilisateurs** sur un site peut attribuer un accès à ce site, mais ne peut pas créer d’autorisation **ASO Manager** à l’échelle de l’organisation.

## Niveaux de fonctionnalité

Chaque fonctionnalité contrôle un type d’action. Ils sont indépendants ; par exemple, vous pouvez accorder Déployer sans modifier.

| Fonction | Ce que cela permet | Ce qu’il ne permet pas |
|---|---|---|
| Mode | Affichez les données du site (opportunités, suggestions, correctifs, rapports et configuration) sans rien modifier. | Toute modification. |
| Modifier | Créer et modifier des opportunités et des suggestions (ce qui doit changer). | Publier des modifications, modifier des paramètres ou gérer des utilisateurs. |
| Déployer | Publiez les correctifs en direct sur le site et annulez-les. | Gestion des utilisateurs. |
| Configurer | Modifiez les paramètres et les connexions du site. | Publication de correctifs ou gestion des utilisateurs. |
| Gérer les utilisateurs et les utilisatrices | Accorder ou révoquer l&#39;accès d&#39;autres membres au site. | Gestion d’un site auquel la personne n’a pas déjà accès |

>[!NOTE]
>
>**La vue est toujours incluse.** Chaque subvention inclut l&#39;option Afficher automatiquement — vous ne pouvez pas gérer, configurer, modifier ou déployer quelque chose que vous ne pouvez pas voir. Pour cette raison, la vue ne peut pas être supprimée seule. Pour supprimer complètement l’accès d’une personne, supprimez le membre (voir [Modifier ou supprimer un membre](#edit-or-remove-a-member) ci-dessous) au lieu de décocher toutes les fonctionnalités.

## Étendue de l’accès aux types d’opportunités

Sur un seul site, vous pouvez accorder l’autorisation Afficher, Modifier et Déployer pour **types d’opportunité spécifiques** (par exemple, Core Web Vitals ou liens internes rompus) plutôt que pour l’ensemble du site. Cela permet à une seule personne de modifier Core Web Vitals tout en ne visualisant que le reste.

- **Affichage**, **Modification** et **Déploiement** peuvent être limités à un ou plusieurs types d’opportunités, ou à **Tous** types d’opportunités.
- Les **Configurer** et **Gérer les utilisateurs** s’appliquent toujours à l’ensemble du site. Elles ne peuvent pas être limitées à un type d’opportunité.

Chaque subvention étendue apparaît comme sa propre ligne pour le membre, avec une colonne **S&#39;applique à** indiquant le type d&#39;opportunité, **Tous** ou **à l&#39;échelle du site**.

>[!CAUTION]
>
>La définition de la portée limite uniquement ce que *cette subvention* donne : elle ne supprime jamais l’accès qu’une autre subvention fournit. Si une personne dispose également d’un accès à l’échelle de l’organisation ou d’une autorisation de type **Tous**, cet accès plus large s’applique toujours. Donc, pour vraiment limiter quelqu&#39;un à des types d&#39;opportunités spécifiques, assurez-vous qu&#39;il ne détient pas également un rôle plus large ou une subvention **tous** types.

## Ajouter un membre

1. Ouvrez l’onglet **Autorisations** (l’icône de cadenas dans le volet de navigation de gauche) et sélectionnez le site.
1. Cliquez sur **Ajouter des membres**.
1. Effectuez une recherche par nom ou adresse e-mail et sélectionnez une ou plusieurs personnes.
1. Sélectionnez le ou les **type(s) d’opportunité)** auxquels l’accès s’applique (ou **tous**), puis sélectionnez les fonctionnalités à accorder.
1. Cliquez sur **Ajouter**.

## Modifier ou supprimer un membre

Dans le tableau **Membres** :

- Cliquez sur **Modifier les fonctionnalités** sur la ligne d’un membre pour modifier ce qu’il peut faire. Lorsque vous modifiez une subvention existante, son type d’opportunité reste fixe : vous modifiez uniquement les fonctionnalités et au moins une fonctionnalité doit rester sélectionnée.
- Cliquez sur **Supprimer** pour révoquer l&#39;accès de ce membre au site.

>[!NOTE]
>
>La modification des fonctionnalités et la suppression d’un membre sont des actions différentes. Pour supprimer tous les accès, utilisez **Supprimer** — vous ne pouvez pas le faire en décochant les fonctionnalités, car une subvention doit conserver au moins une fonctionnalité (et la vue reste toujours).

## Qui peut gérer les autorisations ?

L’onglet **Autorisations** d’un site est disponible pour :

- Membres disposant de la fonctionnalité **Gérer les utilisateurs** sur ce site, et
- Administrateurs de l’organisation (un responsable ASO).

Les membres ne disposant pas de l’autorisation **Gérer les utilisateurs** voient un message indiquant qu’ils ne sont pas autorisés à gérer l’accès à ce site.

## Activer la gestion des utilisateurs et des accès

La gestion des utilisateurs et des accès est contrôlée par un paramètre pour votre organisation. Vous pouvez attribuer un accès avant qu’il ne soit activé, mais il n’est appliqué qu’une **fois** paramètre activé.

Si elle n’est pas encore activée, l’onglet **Autorisations** affiche une bannière vous demandant de contacter votre équipe de compte. Contactez votre équipe de compte Sites Optimizer pour l’activer.

>[!NOTE]
>
>Tant que la gestion des utilisateurs et des accès n’est pas activée, les autorisations que vous attribuez sont enregistrées, mais pas appliquées.

## Configurer l’accès avant application

Il n’est pas nécessaire d’attendre que l’application commence à attribuer l’accès. Même si la gestion des utilisateurs et des accès est toujours **désactivée**, les utilisateurs dotés du rôle **ASO Manager** peuvent ouvrir l’onglet **Autorisations** et affecter des sites et des fonctionnalités à d’autres utilisateurs.

Vous pouvez ainsi préparer à l’avance le bon accès pour tous. Lorsque l’application est ultérieurement activée, vos utilisateurs disposent déjà de l’accès dont ils ont besoin, de sorte que personne ne soit verrouillé de manière inattendue.

>[!IMPORTANT]
>
>Lorsque l’application est désactivée, l’onglet **Autorisations** n’est disponible que pour les utilisateurs d’**ASO Manager**. Configurez d’abord l’accès pour tous vos utilisateurs, puis activez l’application.

## Questions fréquentes

**Les membres au niveau du site ont-ils besoin d’un rôle Admin Console ?**

Non. L’accès au niveau du site est entièrement accordé dans Sites Optimizer, dans l’onglet **Autorisations**. Seuls les rôles à l’échelle de l’organisation sont affectés dans Admin Console.

**Que se passe-t-il si une personne dispose d’un accès à la fois au niveau de l’organisation et du site ?**

Les deux s’appliquent. Leur accès effectif est la combinaison des deux. Les autorisations n’entrent jamais en conflit, car aucune autorisation ne peut refuser l’accès.

**Pourquoi un membre ne peut-il pas créer un responsable à l’échelle de l’organisation avec Gérer les utilisateurs ?**

La création d’un rôle à l’échelle de l’organisation est une action Admin Console. Un membre disposant du droit **Gérer les utilisateurs** peut attribuer l’accès à son propre site, mais seul un administrateur d’organisation peut accorder des rôles à l’échelle de l’organisation.

**Comment puis-je révoquer l’accès d’une personne à un site ?**

Supprimez leur octroi dans l’onglet **Autorisations**. Cela diffère des fonctionnalités d’édition, qui doivent toujours conserver au moins une fonctionnalité.

**Puis-je limiter une personne à des types d’opportunités spécifiques ?**

Oui — accorder l’affichage, la modification ou le déploiement limité à des types d’opportunités spécifiques au lieu de **Tous**. Comme l&#39;accès est cumulatif, il ne prend effet que si la personne ne dispose pas également d&#39;un accès à l&#39;échelle de l&#39;organisation ou d&#39;une autorisation de type **Tous**.
