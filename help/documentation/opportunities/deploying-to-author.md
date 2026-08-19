---
title: Déploiement dans la documentation de création
description: Découvrez comment AEM Sites Optimizer déploie les optimisations sélectionnées dans l’environnement de création et comment les suivre ultérieurement.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 1d55c607aab6c820d014b9a57bfae20b8170c672
workflow-type: tm+mt
source-wordcount: 245
ht-degree: 6%

---

# Déploiement dans la documentation de création

<!--![Deploying to author](./assets/deploying-to-author/hero.png){align="center"}-->

Une fois qu’AEM Sites Optimizer a identifié une opportunité et suggéré des optimisations, vous pouvez examiner et déployer les optimisations sélectionnées pour effectuer d’autres actions.

## Déployer dans l’environnement de création

Sélectionnez une ou plusieurs suggestions dans la liste d’une opportunité, puis cliquez sur **Déployer sur l’instance de création** pour déployer votre sélection, ou **Déployer tout sur l’instance de création** pour déployer toutes les suggestions disponibles en même temps. AEM Sites Optimizer applique uniquement les optimisations sélectionnées à l’environnement de création ; il ne publie pas les modifications sur votre site actif. L’auteur AEM peut ensuite examiner et publier les modifications à partir du système de gestion de contenu (CMS), en cohérence avec le workflow [Optimisation automatique](/help/documentation/opportunities/missing-alt-text.md#auto-optimize) de chaque opportunité.

Cette action est désactivée lorsque vous ne disposez pas des autorisations de déploiement ou lorsque le site n’est pas entièrement configuré pour le déploiement (par exemple, un référentiel de code n’a pas encore été connecté). Dans les deux cas, Sites Optimizer explique pourquoi en regard du bouton Désactivé .

## Suivi des optimisations déployées

<!--![Deployed tab](./assets/deploying-to-author/deployed-tab.png){align="center"}-->

Une fois que vous avez déployé les optimisations sélectionnées, vous pouvez les gérer et effectuer les étapes suivantes à partir de l’onglet **Déployé** de la page des détails de l’opportunité, à côté des onglets **Actuel** et **Ignoré**.

Les mécanismes de déploiement spécifiques, notamment la manière dont les mises à jour sont appliquées pour Edge Delivery Services, AEM as a Cloud Service ou la gestion des ressources numériques, varient selon le type d’opportunité. Consultez la section **Optimisation automatique** de cette opportunité pour plus d’informations.

## Voir aussi

* [Opportunité de texte secondaire manquant](/help/documentation/opportunities/missing-alt-text.md#auto-optimize)
* [Opportunité des valeurs web principales](/help/documentation/opportunities/core-web-vitals.md#auto-optimize)
* [Opportunité de backlinks rompus](/help/documentation/opportunities/broken-backlinks.md#auto-optimize)
