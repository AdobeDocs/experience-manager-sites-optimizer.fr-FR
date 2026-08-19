---
title: Préparation de la documentation sur les correctifs de code
description: Découvrez comment AEM Sites Optimizer prépare les correctifs de code pour Core Web Vitals et comment les suivre par la suite.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: a86d83ee226055e6401b13fd421b40d449b96fa8
workflow-type: tm+mt
source-wordcount: 248
ht-degree: 2%

---

# Préparation de la documentation sur les correctifs de code

<!--![Preparing code patches](./assets/preparing-code-patches/hero.png){align="center"}-->

Pour l’opportunité [Core web vitals](/help/documentation/opportunities/core-web-vitals.md), AEM Sites Optimizer génère des correctifs au niveau du code pour les problèmes de performances identifiés. Vous passez en revue et préparez ces correctifs sous forme de correctifs de code plutôt que de les déployer directement.

## Préparation des correctifs de code

Sélectionnez un ou plusieurs problèmes dans la liste Core Web Vitals, puis cliquez sur **Préparer le correctif de code** pour préparer votre sélection, ou **Préparer tous les correctifs de code** pour préparer tous les correctifs disponibles en une seule fois. AEM Sites Optimizer crée un problème GitHub étiqueté pour chaque correctif et ouvre automatiquement une demande d’extraction liée avec le changement de code, prête à être examinée, testée et fusionnée par votre équipe.

Cette action est désactivée lorsque vous n’êtes pas autorisé à préparer des correctifs de code ou lorsque le site n’est pas entièrement configuré pour cette action, par exemple, lorsqu’aucun référentiel de code n’est connecté ou que la génération de correctifs est toujours en cours. Dans chaque cas, Sites Optimizer explique pourquoi en regard du bouton désactivé .

## Suivi des correctifs de code préparés

Une fois que vous avez préparé les correctifs de code, vous pouvez les gérer et passer à l’étape suivante à partir de l’onglet **Déployé** de la page de détails de Core Web Vitals, avec les onglets **Actuel** et **Ignoré**. L’état d’un correctif à cet endroit indique si sa demande d’extraction a été fusionnée, et pas seulement générée. Un problème ne passe à **Déployé** qu’une fois le correctif fusionné dans votre codebase.

## Voir aussi

* [Opportunité des valeurs web principales](/help/documentation/opportunities/core-web-vitals.md#auto-optimize)
* [Déploiement dans la documentation de création](/help/documentation/opportunities/deploying-to-author.md)
