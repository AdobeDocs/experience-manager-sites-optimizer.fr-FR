---
title: Contrôle en amont des en-têtes
description: Découvrez l’audit Titres dans Contrôle en amont pour AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 9fd898e905bf843b4d39891c5875497a01569791
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%
---
# Audit des titres

L’audit **Titres** examine les sous-titres de votre page (H2 à H6). Il signale les en-têtes qui n’ont pas de texte et les en-têtes qui ignorent un niveau, comme un H2 suivi directement d’un H4.

## Pourquoi est-ce important ?

Les en-têtes donnent à une page son contour. Les lecteurs et lectrices les analysent pour trouver ce dont ils ont besoin, les utilisateurs et utilisatrices de lecteurs d’écran parcourent une page en fonction de ses en-têtes et les moteurs de recherche les utilisent pour comprendre l’organisation du contenu. Un en-tête vide ajoute un arrêt dans ce contour sans rien dedans, et un niveau ignoré rend la structure plus difficile à suivre.

## Ce que l’audit vérifie

L&#39;audit signale une opportunité pour chacun des problèmes suivants :

* **En-tête vide :** un H2, H3, H4, H5 ou H6 qui n’a pas de texte. Un en-tête qui contient uniquement des espaces ou une image est comptabilisé comme vide.
* **Niveau de titre ignoré :** un titre qui est plus d’un niveau plus profond que le titre qui le précède, par exemple un H2 suivi d’un H4, ou un H1 suivi d’un H3. L’opportunité est signalée dans le titre plus profond.

Les deux cas sont signalés à impact modéré.

Les en-têtes H1 sont examinés par l’audit [Metatags](./metatags.md), qui recherche un H1 manquant, vide ou trop long et plusieurs H1 sur une page.

## Lecture des en-têtes

L’audit lit la page que vous modifiez et examine chaque en-tête dans l’ordre dans lequel il apparaît :

* Tous les en-têtes sont comptabilisés, y compris les en-têtes dans l’en-tête, la navigation, le pied de page et les en-têtes masqués à l’écran.
* Seule l’étape d’un en-tête à l’autre est cochée. Une page dont le premier en-tête est un H3 n’est pas marquée pour cela.
* Les en-têtes peuvent remonter un certain nombre de niveaux, par exemple d’un H4 vers un H2.

## Suggestions

Chaque opportunité comprend une recommandation et des conseils fixes pour le changement à apporter. L’audit des en-têtes ne génère pas de suggestions d’IA.

## Si un en-tête avec indicateur vous semble correct

Si une opportunité ne correspond pas à vos attentes, l’un des éléments suivants en est généralement la raison :

* **L’en-tête fait partie de votre modèle de page.** Les en-têtes de l’en-tête, de la navigation ou du pied de page sont vérifiés avec votre contenu, de sorte qu’un en-tête de pied de page qui est plusieurs niveaux plus profond que le dernier en-tête de votre contenu peut être marqué comme un niveau ignoré. La correction de ce problème dans le modèle le résout sur chaque page qui utilise le modèle.
* **L’en-tête contient uniquement une image ou une icône.** Un en-tête sans texte est signalé comme vide même lorsqu’il affiche une image. Ajoutez du texte à l’en-tête ou utilisez un élément sans en-tête pour l’image.

## Limites connues

* **La visibilité n’est pas prise en compte :** les en-têtes masqués à l’écran sont toujours vérifiés.
* **Pages très volumineuses :** les pages comportant plus de 500 en-têtes ne sont pas cochées.

## Comment résoudre

Lorsque l&#39;audit trouve des opportunités, chacune d&#39;elles décrit le problème et le changement recommandé.

* **En-tête vide :** ajoutez un texte descriptif à l’en-tête ou supprimez-le s’il n’est pas nécessaire.
* **Niveau d’en-tête ignoré :** modifiez l’en-tête au niveau inférieur suivant par rapport à l’en-tête qui le précède (par exemple, un H4 après un H2 devient un H3), ou ajoutez le niveau manquant entre les deux.

Utilisez **Mettre en surbrillance sur la page** pour trouver l’en-tête dans votre contenu. La mise en surbrillance de l’en-tête dépend de l’emplacement où vous exécutez le contrôle en amont :

* **Edge Delivery Services :** le contrôle en amont fait défiler l’en-tête et le décrit.
* **AEM Sites Page Editor et Adobe Managed Services (AMS) :** le contrôle en amont fait défiler l’écran jusqu’à l’en-tête et le décrit. La mise en surbrillance nécessite **mode d’édition**.
* **Éditeur universel :** le contrôle en amont sélectionne l’en-tête lui-même ou le bloc modifiable le plus proche qui le contient. Pour un en-tête dans le contenu que l’éditeur ne gère pas, comme la navigation ou un pied de page, le contrôle en amont l’affiche, mais ne peut pas sélectionner l’en-tête lui-même.

Pour plus d’informations, voir [Surligner sur la page](../../audit-results.md#highlight-on-page).

Pour savoir comment examiner et résoudre les opportunités, voir [Résultats d’audit dans le contrôle en amont](../../audit-results.md).
