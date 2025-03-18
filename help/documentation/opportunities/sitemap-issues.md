---
title: Documentation sur l’opportunité des événements du plan du site
description: Découvrez l’opportunité des problèmes du plan du site et comment l’utiliser pour améliorer l’acquisition du trafic.
badgeTrafficAcquisition: label="Acquisition de trafic" type="Caution" url="../../opportunity-types/traffic-acquisition.md" tooltip="Acquisition de trafic"
source-git-commit: d812a49e4b49d329717586b9f3c7a235aff3e69a
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 1%

---


# Opportunité des problèmes de plan de site

![Opportunité des problèmes de plan de site](./assets/sitemap-issues/hero.png){align="center"}

Un plan de site complet et précis permet aux moteurs de recherche d’analyser et d’indexer efficacement les pages du site web, assurant ainsi une meilleure visibilité sur les résultats de recherche. L’opportunité de plan de site identifie les problèmes potentiels avec votre plan de site. La résolution de ces problèmes peut améliorer considérablement l’indexation du moteur de recherche et la visibilité du contenu sur votre site.

Un résumé s’affiche en haut de la page, y compris un résumé du problème et de son impact sur votre site et votre entreprise.

* **Perte de trafic prévue** - Estimation de la perte de trafic due à des problèmes de plan du site.
* **Valeur prévue du trafic** - Valeur estimée du trafic perdu.

## Auto-identification

Les problèmes de plan de site peuvent être filtrés à l’aide des critères suivants :

* **Plan de site avec des problèmes** - URL de plan de site analysée contenant des problèmes potentiels.
* **Type de problème** - Type de problème identifié dans le plan du site :
   * **Erreurs client** - Entrées qui ne renvoient pas de réponse `200 Success`.
   * **Redirections** - Redirections incorrectes ou mal configurées.

>[!BEGINTABS]

>[!TAB Erreurs client]

![Erreurs du client de plan de site d’identification automatique](./assets/sitemap-issues/auto-identify-client-errors.png){align="center"}

Si les URL de votre plan de site renvoient ces informations, les moteurs de recherche peuvent supposer que votre plan de site est obsolète ou que les pages ont été supprimées par erreur. Le client indique que la requête du client (navigateur ou robot d’exploration) n’était pas valide. Les plus courants sont les suivants :

* **404 Introuvable** - La page demandée n&#39;existe pas.
* **403 Interdit** - Le serveur refuse l’accès à la page demandée.
* **410 Gone** - La page a été supprimée intentionnellement et ne reviendra pas.
* **401 Non autorisé** - L&#39;authentification est requise mais non fournie.

Ces erreurs peuvent nuire à l’optimisation pour les moteurs de recherche, en particulier si des pages importantes renvoient des **404 ou 410**, car les moteurs de recherche peuvent les désindexer.

Chaque problème est affiché dans un tableau, avec la colonne **Page** identifiant l’entrée de plan de site concernée :

* **Page** - URL de l’entrée du plan du site présentant un problème.

>[!TAB  Redirections ]

![Erreurs du client de plan de site d’identification automatique](./assets/sitemap-issues/auto-identify-redirects.png){align="center"}

Les plans de site doivent uniquement inclure les URL de destination finale, et non celles qui redirigent. Les redirections sont destinées à guider les utilisateurs et les robots d’exploration vers l’emplacement correct, mais peuvent entraîner des problèmes s’ils sont mal configurés :

* **302 trouvé (redirection temporaire)** - Peut entraîner des problèmes d’optimisation pour les moteurs de recherche s’il est utilisé par erreur au lieu d’un **301**.
* **307 Redirection temporaire** - Similaire à 302, mais conserve la méthode HTTP.
* **Boucles de redirection** - Lorsqu’une page se redirige vers elle-même ou crée une boucle infinie.
* **Redirections rompues** - Lorsqu’une redirection mène à une page inexistante ou 4xx.

Chaque problème est affiché dans un tableau, avec la colonne **Page** identifiant l’entrée de plan de site concernée :

* **Page** - URL de l’entrée du plan du site présentant un problème.

>[!ENDTABS]

## Suggestion automatique

Chaque problème de plan de site [qui répond aux critères de filtrage](#auto-identify) est répertorié dans un tableau avec les colonnes suivantes :

* **Page** - URL de l’entrée du plan du site présentant un problème.
* **Suggestion** - Correctif recommandé pour le problème.

Les suggestions incluent généralement un chemin de site mis à jour pour corriger l’entrée du plan du site. Dans certains cas, ils peuvent également fournir des instructions plus détaillées, telles que la spécification de la cible de redirection correcte.

## Optimisation automatique d’[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}


![Optimisation automatique des problèmes de plan de site](./assets/sitemap-issues/auto-optimize.png){align="center"}

Sites Optimizer Ultimate offre la possibilité de déployer des optimisations automatiques des plans de site.

>[!BEGINTABS]

>[!TAB Déployer l’optimisation]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Demande d’approbation]

{{auto-optimize-request-approval}}

>[!ENDTABS]
