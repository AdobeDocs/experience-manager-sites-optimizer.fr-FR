---
solution: Experience Manager
product: adobe experience manager
type: Documentation
description: Documentation AEM Sites Optimizer.
index: y
git-repo: https://github.com/AdobeDocs/experience-manager-sites-optimizer.fr-FR
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
recommendations: noDisplay
source-git-commit: eda941a0096e32f61b45d69d89a3ee5b1a0c7e4b
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 53%

---


# Métadonnées pour utilisation interne

Les métadonnées dans le système de création GitHub sont hiérarchiques et sont définies selon les niveaux de précédent croissants suivants.

1. metadata.md
1. Table des matières
1. Article

Les métadonnées définies dans le fichier metadata.md s’appliquent à l’intégralité du référentiel, mais peuvent être remplacées aux niveaux de la table des matières et de l’article. Tout remplacement des métadonnées doit être effectué au niveau le plus bas possible.

Les métadonnées du référentiel experience-manager-cloud-service.en sont le minimum requis.

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

Tables des matières

* `sub-product`
* `user-guide-title`

Article

* `title`
* `description`
* `contentOwner` (uniquement sur le contenu des ressources de base sous `/help/assets`)

