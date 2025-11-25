---
source-git-commit: 2f4ef1c6f44d602bfe365a52eb692fe7faa7f05f
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 83%

---
# Instructions relatives à la contribution à la documentation d’Adobe Experience Manager

## Philosophie de la documentation

Les utilisateurs et utilisatrices d’Adobe Experience Manager travaillent dans des environnements très concurrentiels et font de leur mieux afin de créer des expériences numériques qui les distingueront de la concurrence. Par conséquent, lorsqu’Adobe fournit des outils avancés dans AEM, ces outils sont accompagnés d’une documentation précise et claire. Cela permet aux clientes et aux clients de bénéficier immédiatement de leur investissement dans AEM et d’optimiser leur retour sur investissement.

L’objectif de la documentation AEM est de la placer entre les mains des utilisateurs et utilisatrices d’AEM dès que possible. Adobe privilégie donc une documentation précise et compréhensible, et s’emploie à la mettre à jour et à l’améliorer en permanence.

## Contributions à la documentation

Afin d’améliorer continuellement la documentation d’AEM, toute la communauté des utilisateurs d’AEM peut apporter sa contribution. Que ce soit par le biais de demandes d’extraction ou de demandes, les améliorations apportées à la documentation peuvent être des corrections, des clarifications, des extensions et des exemples supplémentaires.

## Normes de la documentation

Bien qu’Adobe apprécie les contributions à sa documentation, toute contribution à la documentation d’AEM, sous la forme d’une demande d’extraction ou d’un problème, doit être conforme aux normes des contributions et de la documentation.

Les contributions qui ne satisfont pas à ces normes peuvent être rejetées.

### Les cas d’utilisation standard sont documentés dans Adobe.

La documentation d’AEM couvre les cas d’utilisation standard. Les cas d’utilisation au-delà de la portée de l’installation et de l’utilisation standard du produit ne font pas partie de la documentation AEM.

### Adobe ne documente généralement pas les bogues ou leurs solutions de contournement

La documentation d’AEM couvre les cas d’utilisation standard. Pour cette raison, les bugs, les effets causés par les bugs et les solutions pour les bugs ne sont pas documentés,

Les exceptions à cette règle s’appliquent aux notes de mise à jour dans lesquelles les problèmes connus peuvent être répertoriés avec les solutions possibles approuvées par la gestion des produits.

### Les contributions à la documentation ne sont pas destinées à répondre aux questions techniques.

Toute contribution susceptible d’améliorer la documentation AEM est la bienvenue. Toutefois, les commentaires, les problèmes et les demandes d’extraction sont destinés uniquement à être des *contributions*. Ils n’ont pas pour but de répondre à vos questions sur l’utilisation et l’implémentation d’AEM ou la résolution de problèmes techniques.

Vous pouvez poser toute question relative à l’utilisation d’AEM ou à des erreurs techniques. Utilisez le processus d’assistance habituel via le [Portail d’assistance Experience Cloud pour entreprises](https://experienceleague.adobe.com/fr?support-solution=General#support) ou discutez-en dans la [communauté Experience Manager](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community?profile.language=fr).

***Les contributions à la documentation d’AEM ne remplacent pas celles du service clientèle d’Adobe*** et toute contribution de ce type visant à obtenir des réponses à des questions d’assistance est refusée.

### Les contributions doivent clairement référencer les pages de documentation concernées.

Si vous créez une demande pour suggérer des améliorations à la documentation, vous devez inclure des liens vers les pages concernées. Si vous créez un problème à l’aide du lien **Modifier cette page** sur une page de documentation, le problème est créé automatiquement avec un lien vers la page.

Cette méthode ne s’applique pas aux requêtes d’extraction qui, par nature, font référence aux pages concernées.

## Directives relatives à la documentation

Toute contribution à la documentation d’AEM doit respecter certaines instructions de style.

Le respect de ces instructions facilite la révision de votre contribution et, par conséquent, l’intégration à la documentation d’AEM est plus rapide.

### Langue et style

#### Langue

* La documentation AEM est créée et conservée en anglais américain.
* Veillez à ce que les expressions restent le plus simple possible.
* Restez clair et concis.

Souvenez-vous que les lecteurs de la documentation d’AEM sont internationaux et ne peuvent pas être des locuteurs anglais natifs ou bilingues. Évitez les expressions familières et faites preuve d’autant de clarté et de simplicité que possible.

#### Suivre le guide de style Microsoft®

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

Dans la mesure du possible, évitez toute référence directe à une version spécifique dans tout le contenu de la documentation. Cette recommandation rend la documentation plus flexible et extensible pour les versions ultérieures.

### Utiliser Day, AEM, CQ, CRX

Dans un article, faites toujours référence au produit par son nom complet, **Adobe Experience Manager**, la première fois que celui-ci est mentionné. Par la suite, il peut être appelé **AEM**.

N’utilisez pas les termes Day, Day Software, CQ et CRX, sauf lorsque c’est inévitable, comme dans les noms de classe ou en référence à l’historique d’AEM.
