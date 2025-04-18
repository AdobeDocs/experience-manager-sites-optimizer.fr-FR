---
title: Documentation sur l’opportunité des autorisations du site web
description: Découvrez l’opportunité des autorisations du site web et comment l’utiliser pour renforcer la sécurité de votre site web.
badgeSecurityPosture: label="Posture de sécurité" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Posture de sécurité"
source-git-commit: c99bd0ab418c1eb0693f39ea16ee41f8a1263099
workflow-type: ht
source-wordcount: '218'
ht-degree: 100%

---


# Opportunité des autorisations du site web

![Opportunité des autorisations du site web](./assets/website-permissions/hero.png){align="center"}

L’opportunité des autorisations du site web optimise les autorisations du site web, essentielles pour maintenir un environnement AEM sécurisé et gérable. Cette opportunité vous permet d’affiner les contrôles d’accès en supprimant les autorisations trop étendues, telles que `jcr:all` sur des chemins d’accès génériques tels que `/` ou `/content`, et en alignant l’accès des utilisateurs et utilisatrices sur le principe de moindre privilège. En rationalisant les autorisations et en éliminant les redondances, vous pouvez réduire les risques de sécurité, améliorer la maintenabilité et empêcher de futures erreurs de configuration. Agissez en examinant et en mettant à jour les autorisations dans la console Autorisations de sécurité d’AEM ou dans votre référentiel de code, pour vous assurer que les utilisateurs et utilisatrices du service disposent uniquement de l’accès réellement nécessaire.

## Identification automatique

![Identification automatique des autorisations du site web](./assets/website-permissions/auto-identify.png){align="center"}

La fonctionnalité **Opportunité des autorisations du site web** identifie et répertorie automatiquement les éléments suivants :

* **Utilisateur ou utilisatrice** : compte de l’utilisateur ou utilisatrice disposant de l’autorisation suspecte.
* **Chemin d’accès** : chemin d’accès dans AEM affecté par l’autorisation.
* **Autorisation** : autorisation suspecte.
* **Problème** : indique le type de problème ayant un impact sur l’autorisation.

## Suggestion automatique

![Suggestion automatiquement des vulnérabilités du site web](./assets/website-permissions/auto-suggest.png){align="center"}

La suggestion automatique fournit des recommandations générées par l’IA dans le champ **Autorisations suggérées**, ce qui vous permet de remplacer toutes les autorisations marquées par des alternatives sécurisées.

## Optimiser automatiquement

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

![Optimisation automatique des autorisations du site web](./assets/website-permissions/auto-optimize.png){align="center"}

Sites Optimizer Ultimate permet de déployer une optimisation automatique pour les vulnérabilités détectées.

>[!BEGINTABS]

>[!TAB Déployer l’optimisation]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Demande d’approbation]

{{auto-optimize-request-approval}}

>[!ENDTABS]
