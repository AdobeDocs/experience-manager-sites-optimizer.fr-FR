---
solution: Experience Manager
product_v2: id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
usetq: true
product: adobe experience manager
landing-page-name: experience-manager
landing-page-breadcrumb-title: AEM
type: Documentation
description: Documentation AEM Sites Optimizer.
index: true
git-repo: https://github.com/AdobeDocs/experience-manager-sites-optimizer.en
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
recommendations: noDisplay
source-git-commit: b6745249d9a773ce875f421dd16947a1a4d0a245
workflow-type: tm+mt
source-wordcount: 85
ht-degree: 2%

---


# Métadonnées à usage interne

Le système de création GitHub organise les métadonnées de manière hiérarchique, en utilisant les niveaux de précédent croissants suivants.

1. metadata.md
1. ToC
1. Article

Les métadonnées définies dans le fichier metadata.md s’appliquent à l’ensemble du référentiel, mais elles peuvent être remplacées au niveau de la table des matières et de l’article. Tout remplacement des métadonnées doit être effectué au niveau le plus bas possible.

Les métadonnées du référentiel `experience-manager-cloud-service.en` sont le minimum requis.

metadata.md

* `product`
* `git-repo`
* `index`
* `solution-title`
* `solution-hub-url`
* `getting-started-title`
* `getting-started-url`
* `tutorials-title`
* `tutorials-url`

ToCs

* `sub-product`
* `user-guide-title`

Article

* `title`
* `description`
* `contentOwner` (uniquement sur le contenu des ressources de base sous `/help/assets`)

