---
title: Documentation sur l’opportunité d’autorisations de site web
description: Découvrez l’opportunité d’autorisations du site web et comment l’utiliser pour renforcer la sécurité de sur votre site web.
badgeSecurityPosture: label="Position de sécurité" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Position de sécurité"
source-git-commit: c99bd0ab418c1eb0693f39ea16ee41f8a1263099
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 2%

---


# Opportunité d’autorisations de site web

![Opportunité d’autorisations de site web](./assets/website-permissions/hero.png){align="center"}

L’opportunité Autorisations du site web optimise les autorisations du site web, essentielles pour maintenir un environnement AEM sécurisé et gérable. Cette opportunité vous permet d’affiner les contrôles d’accès en supprimant les autorisations trop générales, telles que les `jcr:all` sur des chemins d’accès génériques tels que `/` ou `/content`, et en alignant l’accès des utilisateurs et utilisatrices sur le principe de moindre privilège. En rationalisant les autorisations et en éliminant les redondances, vous pouvez réduire les risques de sécurité, améliorer la maintenabilité et empêcher de futures erreurs de configuration. Agissez en examinant et en mettant à jour les autorisations dans la console Autorisations de sécurité d’AEM ou dans votre référentiel de code, en vous assurant que les utilisateurs du service disposent uniquement de l’accès dont ils ont réellement besoin.

## Auto-identification

![Identification automatique des autorisations du site web](./assets/website-permissions/auto-identify.png){align="center"}

La fonctionnalité **Autorisations de site web** identifie et répertorie automatiquement

* **Utilisateur** - Compte utilisateur disposant de l’autorisation suspecte.
* **Path** - Chemin d’accès dans AEM affecté par l’autorisation.
* **Autorisation** - Autorisation suspecte.
* **Problème** - Indique le type de problème ayant un impact sur l’autorisation.

## Suggestion automatique

![Suggérer automatiquement des vulnérabilités de site web](./assets/website-permissions/auto-suggest.png){align="center"}

La suggestion automatique fournit des recommandations générées par l’IA dans le champ **Autorisations suggérées**, ce qui vous permet de remplacer toutes les autorisations marquées par des alternatives sécurisées.

## Optimisation automatique

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

![Optimisation automatique des autorisations de site web](./assets/website-permissions/auto-optimize.png){align="center"}

Sites Optimizer Ultimate offre la possibilité de déployer une optimisation automatique pour les vulnérabilités détectées.

>[!BEGINTABS]

>[!TAB Déployer l’optimisation]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Demande d’approbation]

{{auto-optimize-request-approval}}

>[!ENDTABS]
