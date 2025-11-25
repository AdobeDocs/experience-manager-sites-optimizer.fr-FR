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
source-git-commit: 2f4ef1c6f44d602bfe365a52eb692fe7faa7f05f
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 29%

---


# Métadonnées pour utilisation interne

Le système de création GitHub organise les métadonnées de manière hiérarchique, en utilisant les niveaux de précédent croissants suivants.

1. metadata.md
1. Table des matières
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

Tables des matières

* `sub-product`
* `user-guide-title`

Article

* `title`
* `description`
* `contentOwner` (uniquement sur le contenu des ressources de base sous `/help/assets`)

