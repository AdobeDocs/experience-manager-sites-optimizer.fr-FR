---
title: Documentation sur l’opportunité des valeurs web principales
description: Découvrez l’opportunité des valeurs web principales et comment l’utiliser pour améliorer l’acquisition du trafic.
badgeSiteHealth: label="Intégrité du site" type="Caution" url="../../opportunity-types/site-health.md" tooltip="Intégrité du site"
source-git-commit: fd992e5f4508ccd4236757167a16c744d98cc6ae
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 6%

---


# Opportunité des valeurs web principales

<!--![core web vitals opportunity](./assets/core-web-vitals/hero.png){align="center"}-->

>[!VIDEO](https://video.tv.adobe.com/v/3483373/?captions=fre_fr&learn=on&enablevpops)

L’opportunité Core Web Vitals identifie les pages de votre site web qui ne sont pas performantes, ce qui a un impact sur l’expérience utilisateur et les performances de recherche organiques. Ces problèmes peuvent provenir de facteurs tels que les polices personnalisées, les dépendances JavaScript non optimisées et les scripts tiers. Core Web Vitals mesure la vitesse de chargement du contenu, la stabilité de la mise en page et la réactivité de la page aux interactions utilisateur.

AEM Sites Optimizer détecte les pages affectées par ces problèmes, fournit des recommandations d’IA spécifiques au niveau du code et applique des correctifs par le biais de vos workflows de développement existants. Notez que seules les pages comportant au moins 1 000 pages vues peuvent être analysées.

## Identification automatique

<!--![Auto-identify core web vitals](./assets/core-web-vitals/auto-identify.png){align="center"}-->

AEM Sites Optimizer surveille en permanence les performances du site à l’aide de la [télémétrie opérationnelle](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/sites/operational-telemetry-for-aem-as-a-cloud-service) pour détecter les régressions dans les mesures Core Web Vitals telles que Largest Contentful Paint (LCP), Cumulative Layout Shift (CLS) et Interaction to Next Paint (INP). Il utilise des données utilisateur réelles pour identifier les régressions de performances et hiérarchise les problèmes en fonction de leur impact sur l’expérience utilisateur.

AEM Sites Optimizer affiche la liste de tous les problèmes courants, détaillée par mobile et poste de travail. La colonne **Page** indique l’entrée de page concernée et les problèmes sont classés par LCP, INP et CLS.

## Suggestion automatique

<!--![Auto-suggest core web vitals opportunity](./assets/core-web-vitals/auto-suggest.png){align="center"}-->

Pour chaque problème identifié, AEM Sites Optimizer génère des recommandations normatives au niveau du code afin d’améliorer les performances de Core Web Vitals. Il évalue l’implémentation sous-jacente en accédant à votre référentiel de code. Cela permet au système d’analyser la manière dont les composants, les scripts et les styles sont implémentés et d’identifier la cause première des problèmes de performances. Sur la base de cette analyse, le système fournit des recommandations ciblées et génère des correctifs de code qui spécifient les modifications nécessaires pour améliorer les performances. Chaque recommandation peut être examinée avant d’être appliquée.

Lorsque vous cliquez sur le bouton de suggestion, une nouvelle fenêtre s’affiche, qui contient les mesures de performances LCP, INP et CLS comme catégories. Vous pouvez basculer entre ces catégories pour afficher la liste des problèmes spécifiques. Chaque catégorie peut contenir plusieurs problèmes. Veillez donc à faire défiler l’écran vers le bas pour afficher la liste complète des problèmes et des recommandations. En outre, il existe deux jauges de performances pour les appareils mobiles et les ordinateurs de bureau pour chaque mesure.

## Optimiser automatiquement

<!--[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}-->

Une fois les recommandations examinées et approuvées, vous pouvez cliquer sur **Déployer l’optimisation**. AEM Sites Optimizer génère des correctifs de code en fonction des problèmes identifiés et les rend disponibles par le biais de processus de contrôle de version. Le processus d’optimisation comprend les étapes suivantes :

* **Création de problème** - Crée un problème GitHub étiqueté pour chaque correctif, y compris une description claire et l’URL affectée pour la visibilité.
* **Diffusion de demande d’extraction** - Ouvre automatiquement une demande d’extraction liée avec le correctif de code exact, prête à être examinée, testée et fusionnée.
* **Suivi de l’état** - Effectue le suivi de chaque correctif jusqu’à la fin, en signalant les tentatives de suivi partielles ou ayant échoué.

Avant de rendre ces mises à jour disponibles, AEM Sites Optimizer effectue une validation pour s’assurer que les correctifs corrigent le problème sous-jacent et n’introduisent pas de régressions. Toutes les mises à jour suivent les pratiques de développement standard, qui nécessitent une révision et une approbation avant d’être fusionnées en production.

Cela permet de s’assurer que les optimisations de performances sont exactes, validées et intégrées aux processus de développement et de gouvernance existants.
