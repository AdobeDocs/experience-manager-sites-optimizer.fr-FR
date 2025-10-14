---
source-git-commit: 505238dcbe7fa9c1ee22dd174d6641e7df10394f
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 69%

---
# Instructions relatives à la contribution à la documentation d’Adobe Experience Manager

## Philosophie de la documentation

Les utilisateurs de Adobe Experience Manager travaillent dans des environnements hautement compétitifs et s’efforcent de créer des expériences digitales qui les distingueront de leurs concurrents. Par conséquent, lorsqu’Adobe fournit de nouveaux outils avancés dans AEM, il est essentiel que ces outils soient complétés par une documentation précise et claire pour permettre à la cliente ou au client d’exploiter immédiatement son investissement AEM et maximiser le ROI.

L’objectif de la documentation AEM est de la placer entre les mains des utilisateurs et utilisatrices d’AEM dès que possible. Par conséquent, l’équipe de documentation d’AEM donne la priorité à une documentation précise et utilisable et s’efforce de la mettre à jour et de l’améliorer en permanence.

## Contributions à la documentation

Afin d’améliorer continuellement la documentation d’AEM, toute la communauté des utilisateurs d’AEM peut apporter sa contribution. Que ce soit par le biais de demandes d’extraction ou de demandes, les améliorations apportées à la documentation peuvent être des corrections, des clarifications, des extensions et des exemples supplémentaires.

## Normes de la documentation

Bien que l’équipe de documentation d’Experience Manager accueille favorablement les contributions à la documentation d’Adobe, toute contribution à la documentation d’AEM, que ce soit sous la forme d’une demande d’extraction ou d’un problème, doit être conforme aux normes de contribution et de documentation de l’équipe.

Les contributions qui ne satisfont pas à ces normes peuvent être rejetées.

### L’équipe de documentation d’Experience Manager documente les cas d’utilisation standard.

La documentation d’AEM couvre les cas d’utilisation standard. Les cas d’utilisation au-delà de la portée de l’installation et de l’utilisation standard du produit ne font pas partie de la documentation AEM.

### L’équipe de documentation d’Experience Manager ne documente généralement pas les bogues ou leurs solutions.

La documentation d’AEM couvre les cas d’utilisation standard. Pour cette raison, les bugs, les effets causés par les bugs et les solutions pour les bugs ne sont pas documentés,

Les exceptions à cette règle concernent les notes de mise à jour qui répertorient les problèmes connus ainsi que les solutions possibles après approbation par l’équipe de gestion des produits AEM.

### Les contributions à la documentation ne sont pas destinées à répondre aux questions techniques.

Toute opinion susceptible d’améliorer la documentation AEM est la bienvenue sous forme de contributions. Toutefois, les commentaires, les demandes et les demandes d’extraction sont destinés uniquement aux *contributions*. Leur finalité n’est pas de répondre à vos questions sur l’utilisation et la mise en œuvre d’AEM ou la résolution de problèmes techniques.

Toute question relative à l’utilisation d’AEM ou à la résolution d’erreurs techniques doit être soumise au moyen du processus d’assistance classique via le [Portail d’assistance d’Experience Manager](https://experienceleague.adobe.com/fr?support-solution=Experience+Manager&lang=fr#home) ou posée à la [communauté Experience Manager](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community?profile.language=fr).

***Les contributions à la documentation d’AEM ne remplacent pas celles du service clientèle d’Adobe*** et toute contribution de ce type visant à obtenir des réponses à des questions d’assistance est refusée.

### Les contributions doivent clairement référencer les pages de documentation concernées.

Si vous créez une demande pour suggérer des améliorations à la documentation, vous devez inclure des liens vers les pages concernées. Si vous créez un problème à l’aide du lien **Modifier cette page** sur une page de documentation, le problème sera créé automatiquement avec un lien vers la page.

Cela ne s’applique pas aux requêtes d’extraction, car ces dernières, de par leur nature, font référence aux pages affectées.

## Directives relatives à la documentation

Toute contribution à la documentation d’AEM doit respecter certaines instructions de style.

Le respect de ces instructions facilite la révision de votre contribution et, par conséquent, l’intégration à la documentation d’AEM est plus rapide.

### Langue et style

#### Langue

* La documentation AEM est créée et conservée en anglais américain.
* Veillez à ce que les expressions restent le plus simple possible.
* Restez clair et concis.

Souvenez-vous que les lecteurs de la documentation d’AEM sont internationaux et ne peuvent pas être des locuteurs anglais natifs ou bilingues. Évitez les expressions familières et restez aussi clair et simple que possible.

#### Suivi du guide de style Microsoft®

[Le guide de style Microsoft®](https://learn.microsoft.com/en-us/style-guide/welcome/) est gratuit et concerne la documentation logicielle. Il s’applique à la documentation AEM, dans la mesure du possible.

### Mise en forme

| Élément | Style |
|---|---|
| Élément ou option de l’interface utilisateur | **gras** |
| Nom de fichier, chemin, entrée utilisateur, paramètre-valeurs | `monospaced` |
| Code, ligne de commande | ```Code Block``` |

### Captures d’écran

Les captures d’écran doivent être utilisées de manière judicieuse et uniquement lorsqu’une description textuelle est insuffisante.

N’utilisez pas de marqueurs ni d’autres annotations dans les captures d’écran (comme les cadres rouges, les flèches ou le texte). Ainsi, les captures d’écran sont plus faciles à réutiliser ou à répliquer dans les versions localisées de la documentation.

### Références spécifiques à la version

Dans la mesure du possible, évitez toute référence directe à une version spécifique dans tout le contenu de la documentation. La documentation est ainsi plus flexible et extensible pour les versions ultérieures.

### Utilisation de Day, AEM, CQ, CRX

Le produit doit toujours être appelé par son nom complet **Adobe Experience Manager** pour la première fois dans un article et peut ensuite être appelé **AEM**.

N’utilisez pas les termes Day, Day Software, CQ et CRX, sauf lorsque c’est inévitable, comme dans les noms de classe ou en référence à l’historique d’AEM.
