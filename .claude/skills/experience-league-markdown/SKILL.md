---
name: experience-league-markdown
description: 'À utiliser lors de l’écriture ou de la modification de fichiers Markdown dans un référentiel Adobe Experience League / Adobe-Enterprise-Docs (help/**/*.md) : régit le front-issue, les en-têtes, les notes (NOTE/TIP/IMPORTANT/WARNING/etc.), les onglets (BEGINTABS/TAB/ENDTABS), les incorporations vidéo, les badges, les images, les liens/références croisées, les tableaux, les listes, les blocs de code et la liste autorisée de balises HTML restreinte que le pipeline de validation d’Experience League applique.'
source-git-commit: 14f10c231373992c49a8bb93c043556305b6280d
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 2%

---


# Experience League Markdown

## Vue d’ensemble

Les documents Experience League utilisent Markdown parfumé GitHub ainsi qu’un ensemble d’extensions personnalisées (shortcodes basés sur des guillemets-blocs, badges, onglets, incorporations vidéo). Le pipeline de création **valide** ces fichiers ; l’utilisation d’une syntaxe non prise en charge (balises de `<video>` brutes, `<hr>`, listes de tâches, puces variées, niveaux d’en-tête ignorés, images surdimensionnées) entraîne une erreur de création/validation, et pas seulement une unité de style.

Source de vérité : https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/markdown-syntax (récupérez cette page si le fichier local reference.md semble obsolète — la date de « Dernière mise à jour » est en haut).

Référence de syntaxe complète avec chaque shortcode et règle : [reference.md](reference.md). Lisez-le avant d’écrire tout ce qui n’est pas anodin (onglets, vidéo, badges, tableaux avec HTML).

## Référence rapide

| Elément | Syntaxe | Notes |
|---|---|---|
| Matière Première | `---\ntitle: ...\ndescription: ...\n---` | Ligne vide, `# Title` doit venir ensuite |
| Niveaux de titre | `#`, `##`, `###` | `#` = titre (correspond aux `title` frontMATTER), `##` = entrées de mini-table des matières. Ne sautez jamais un niveau. Ligne vide avant/après. Max 69 chars (FR) |
| ID d’en-tête | `## Heading text {#custom-id}` | Obligatoire si le titre commence par/contient un chiffre, par exemple `## 2026 release notes {#2026-release-notes}` |
| Remarque/Conseil/etc. | `>[!NOTE]` puis `>` puis `>Text` (chacun sur sa propre ligne) | Types : REMARQUE, CONSEIL, IMPORTANT, AVERTISSEMENT, ATTENTION, ADMINISTRATEUR, DISPONIBILITÉ, CONDITIONS PRÉALABLES, INFOS, ERREUR, SUCCÈS |
| Onglets | `>[!BEGINTABS]` / `>[!TAB Title]` / `>[!ENDTABS]` | Impossible d’imbriquer des ensembles d’onglets. Impossible d’imbriquer dans des listes. |
| Vidéo | `>[!VIDEO](https://video.tv.adobe.com/v/ID/?learn=on&enablevpops)` | Doit être hébergé sur video.tv.adobe.com — aucun lien de `<video>`/fichier brut |
| Image | `![alt text](assets/img.png "hover text"){width="300" align="center"}` | `align` est `center` ou `right` uniquement (aucun `left`, aucun `valign`) |
| Lien (relatif) | `[Text](../folder/file.md)` | Compte d’emplacement du fichier source |
| Lien (racine) | `[Text](/help/guide/file.md)` | Fonctionne depuis n’importe quel emplacement du référentiel. Obligatoire pour les URL de badge TOC.md. |
| Lien profond | `[Text](file.md#heading-id)` | L’en-tête cible nécessite une `{#heading-id}` explicite |
| Lien externe (URL nue) | `<https://example.com>` | Les URL nues ne sont PAS liées automatiquement : elles sont encapsulées dans des `< >` ou utilisées `[text](url)` |
| Liste à puces | `* item` (choisissez l’une des options `*`/`-`/`+`, restez cohérent) | Ligne vide avant/après la liste ; marqueurs de mélange = erreur de validation |
| Liste numérotée | `1. item` (répétez `1.` chaque ligne) | GitHub effectue le rendu des nombres réels |
| Code (inline) | `` `code` `` | Pour les noms de fichiers, les commandes, les valeurs et les exemples d’URL non validés |
| Code (clôturé) | ` ```language ` ... ` ``` ` | Toujours spécifier une langue ; ligne vide avant/après ; `{line-numbers="true" start-line="n" highlight="n-m"}` facultatif |
| Badge (intégré) | `[!BADGE Beta]{type=Informative url="..." tooltip="..."}` | `type` : Informatif/Positif/Négatif/Neutre/Prudence |
| Réductible | `+++Summary` ... `+++` | Aucun élément réductible imbriqué ; lignes vides autour des listes/codes internes |
| Ligne vierge vers l&#39;arrière | `<br>&nbsp;` sur sa propre ligne | Les lignes vides supplémentaires simples sont réduites/ignorées par le moteur de rendu |
| Commentaire | `<!-- text -->` | Jamais `<!--> text <-->` : visible par toute personne affichant le fichier brut sur GitHub, donc aucun secret |

## Erreurs courantes

- **Erreur de validation du `<video>` brut, du `<iframe>` ou d’un autre HTML non** →. La HTML placer sur la liste autorisée est la suivante : `table tbody td tfoot thead th tr col colgroup p ul ol li br b caption i strong u s span sub sup a img div em pre code codeblock`. Toute autre chose (y compris `<video>`/`<source>`) est rejetée. Utilisez plutôt le shortcode `>[!VIDEO]`, qui nécessite que la vidéo soit déjà hébergée sur video.tv.adobe.com.
- **`<hr>`/`***` les règles horizontales, les codes courts d&#39;émoticônes (`:bowtie:`), les listes de tâches (`- [x]`)** — aucun n&#39;est pris en charge ; ne les utilisez pas même si un aperçu local les affiche.
- **Combinaison de puces** (`*` et `-` dans la même liste) — erreur de validation. Choisissez-en un par article.
- **Ne pas tenir compte des niveaux de cap** (`##` directement à `####`) — interdit.
- **Un en-tête de début numérique sans ID explicite** (par exemple `## 2026 release notes`) — doit ajouter des `{#some-id}` ou le rappel automatique peut entrer en collision/rupture.
- **URL nues en prose** (`Visit https://example.com for more`) — ne s’affiche pas sous forme de lien. Enveloppez-le dans un `< >` ou utilisez-le `[text](url)`.
- **Lignes vierges supplémentaires pour l’espacement visuel** — réduites par le moteur de rendu. Utilisez des `<br>&nbsp;` au lieu d’un `<br>` nu ou de nouvelles lignes répétées.
- **Images de plus de 5 Mo** — avertissement de validation à 5 Mo, erreur à 20 Mo. Plus de 100 images dans un article interrompent le rendu (limite EDS).
- **Plus de deux badges dans les métadonnées de frontMATTER** — non autorisé par défaut.
- **Échappement des problèmes** : la barre oblique inverse ne fonctionne que pour les `` # { } [ ] * + - . ! ``. Pour `<` `>` dans des éléments tels que des espaces réservés `<filename>`, utilisez un bloc de code intégré ou des entités HTML (`&lt;filename&gt;`), et non une barre oblique inverse.

## Avant de valider les modifications Markdown

1. Frontmaterial présent, `# Title` suit immédiatement (après la ligne vide).
2. Chaque en-tête comporte une ligne vide avant et après ; aucun niveau ignoré.
3. Toute vidéo est `>[!VIDEO](https://video.tv.adobe.com/...)`, et non une balise `<video>` brute.
4. Tout code court personnalisé (`>[!NOTE]`, `>[!BEGINTABS]`, `>[!BADGE ...]`) correspond à la syntaxe exacte dans [reference.md](reference.md), y compris la ligne de `>` vide à l’intérieur des blocs multilignes.
5. Les listes utilisent un style de puces/nombres cohérent, avec des lignes vides autour de la liste entière.
6. Liens : les liens relatifs sont résolus à partir du dossier du fichier *source* ; les liens entre référentiels croisés ou table des matières/badges utilisent le formulaire relatif à la racine (`/help/...`).
7. Aucune balise HTML en dehors de la liste autorisée  dans la section Erreurs courantes ci-dessus.
