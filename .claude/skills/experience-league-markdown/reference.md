---
source-git-commit: 14f10c231373992c49a8bb93c043556305b6280d
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 0%

---
# Experience League Markdown - Référence de syntaxe complète

Condensé de https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/markdown-syntax (dernière confirmation par rapport à la page « Dernière mise à jour : 17 juin 2026 »). Récupérez à nouveau la page active si quelque chose ici semble obsolète.

## FrontMATTER et title

```markdown
---
title: Title for search optimization
description: This is the article description used for search optimization.
---
# Article title
```

La ligne immédiatement après la `---` de fermeture (et une ligne vide) doit être la `# Title` — et elle doit correspondre à `title:` dans le devant.

## Mise en forme de texte de base

- Gras : `**bold**`
- Italique : `*italic*`
- Gras+italique : `***both***`
- Échapper un graphique de mise en forme : `\*not italic\*`
- Les paragraphes n’ont pas besoin de syntaxe spéciale, seulement d’une ligne vide entre eux.

## Titres

```markdown
# This is level 1 (article title)
## This is level 2 (mini-TOC entry)
### This is level 3
```

- `#` (H1) = titre de l’article, doit correspondre à la `title` frontMATTER.
- `##` (H2) = apparaît par défaut dans la mini-table des matières (`mini-toc-levels: 3` dans le frontMATTER pour afficher plus de niveaux).
- Ne jamais sauter un niveau (`##` → `####` n&#39;est pas valide).
- Ligne vide requise avant **et** après chaque en-tête.
- Longueur maximale du titre : 69 caractères (EN), 120 caractères (localisé).
- ID d’en-tête/ancre : `## Creating processing rules {#processing-rules}` — minuscules, avec traits d’union. Obligatoire si le texte de l’en-tête commence par un chiffre (par exemple, année). Sans ID explicite, l’ancre par défaut est le texte de l’en-tête qui a été sélectionné automatiquement.

## Remarques/avertissements

Types standard : `NOTE`, `TIP`, `IMPORTANT`, `WARNING`. Nouveaux types EXL uniquement : `ADMIN`, `AVAILABILITY`, `PREREQUISITES`, `INFO`, `ERROR`, `SUCCESS`.

```markdown
>[!NOTE]
>
>This is a standard NOTE block.
>
>It can include multiple paragraphs.
```

Chaque ligne du bloc commence par `>`. Insérez une ligne de `>` nue juste après le marqueur de type.

## Onglets

```markdown
>[!BEGINTABS]

>[!TAB iOS]

Content for the iOS tab.

>[!TAB Android]

Content for the Android tab.

>[!ENDTABS]
```

- Impossible d’imbriquer des ensembles d’onglets dans des ensembles d’onglets ou des ensembles d’onglets dans des listes.
- Les titres des onglets sont rendus textuellement, sans mise en forme Markdown dans `>[!TAB ...]`.
- Plusieurs ensembles d’onglets peuvent être affichés sur une page.

## Vidéo

```markdown
>[!VIDEO](https://video.tv.adobe.com/v/27069/?learn=on&enablevpops)
```

- La vidéo doit déjà être hébergée sur `video.tv.adobe.com` (Adobe TV/MPC). Les liens de fichiers vidéo bruts ou les balises `<video>` ne sont pas pris en charge.
- Paramètres de requête recommandés : `?learn=on&enablevpops` (formulaire canonique utilisé par chaque élément incorporé dans ce référentiel). Ajoutez des `&autoplay=true` à la lecture automatique.
- Transcriptions : ajoutez des `{transcript=true}` au shortcode ou définissez des `auto-video-transcripts: true` dans `TOC.md`/`metadata.md` pour l’ensemble du guide/référentiel.

## Badges

Badge intégré (s’affiche lorsqu’il est placé) :

```markdown
[!BADGE Beta]{type=Informative url="https://www.example.com" tooltip="Go to example.com"}
```

Badge de métadonnées (rendu au-dessus du H1) — en frontMATTER :

```yaml
badgePremium: label="Premium" type="Positive" url="https://www.premium-product.com" tooltip="Download Premium"
```

- `type` (non-respect de la casse) : `Informative` (par défaut/bleu), `Positive` (vert), `Negative` (rouge), `Neutral` (gris foncé), `Caution` (jaune).
- Seul le libellé est requis ; `type`/`url`/`tooltip` facultatif.
- Max. **deux** de badges de métadonnées par article (configurable, mais à demander avant de se fier à une exception).
- Les valeurs des badges de métadonnées doivent être citées. Le badge intégré `url`/`tooltip` doit être entre guillemets.
- Les URL de badge utilisées à partir de `TOC.md` doivent être relatives à la racine (`/help/guide/article.md`), et non relatives. Les entrées de la table des matières s’appliquent à tous les dossiers.
- `before-title="false"` déplace un badge de métadonnées sous le H1.
- Ajoutez `newtab=true` pour ouvrir l’URL du badge dans un nouvel onglet.

## Images

```markdown
![alt text](assets/logo.png "Hover text"){width="300" align="center"}
```

- `align` : `center` ou `right` uniquement — pas de `left`, pas de `valign`.
- `width` : pixels (`"300"`) ou pourcentage de la zone de vue (`"50%"`).
- `zoomable="yes"` permet à l’image de cliquer pour l’agrandir (ne la combinez pas à une image qui est également un lien, le lien gagne).
- Chemin relatif à la racine pour les images partagées : `/help/assets/imagename.png`.
- Limites : 100 Mo de limite stricte (GitHub), 5 Mo avant que vous ne commenciez à vous en soucier, 20 Mo déclenchent une erreur de validation. 100 images maximum par article (limite de rendu EDS).

## Liens et références croisées

- Externe : `[Adobe](https://www.adobe.com)`
- URL nue comme lien : `<https://www.adobe.com>` — une URL nue non encapsulée ne se lie **pas** automatiquement.
- Référence croisée relative : `[Overview](collaborative-doc-instructions/overview.md)` - résolution à partir de l’emplacement du fichier *source* ; prend en charge `./`, `../`, `../../`.
- Référence croisée relative à la racine : `[Overview](/help/using/docile-rules/introduction.md)` - fonctionne à partir de n’importe quel fichier du référentiel, quel que soit l’emplacement source.
- Lien profond vers un en-tête : la cible a besoin d’`{#heading-id}` ; lien avec `[Text](file.md#heading-id)` (ou simplement `#heading-id` pour une même page).
- Ouvrir dans un nouvel onglet : `[See What's new](whats-new.md){target="_blank"}`.

## Listes

```markdown
1. This is step 1.
1. This is the next step.
   1. Sub-step (indent 3 spaces for numbered lists)
   1. Sub-step
```

```markdown
* First item.
* Second item.
```

- Listes numérotées : toujours écrire `1.` (ou toujours `1)`) — GitHub effectue le rendu de la séquence réelle. Choisissez un style (`.` ou `)`) et restez cohérent dans l’article.
- Listes à puces : choisissez l’une des puces `*`, `-`, `+` et restez cohérent ; les mélanger dans le même article est une erreur de validation. Convention dans la plupart des référentiels : `*`.
- Ligne vierge requise avant et après toute liste.
- Le contenu entre les éléments de la liste (images, tableaux, notes) doit être mis en retrait au début du texte (3 espaces pour les listes numérotées, 2 pour les listes à puces) ou il rompt la liste. La surmise en retrait (6 espaces) la transforme en bloc de code.

## Blocs de code

Inline : `` `code` `` — ou placez en triple backticks inline si vous avez besoin d&#39;un backtick littéral à l&#39;intérieur.

Clôturé :

````markdown
```javascript
var x = 1;
```
````

- Spécifiez toujours une langue pour la mise en surbrillance de la syntaxe + le bouton Copier .
- Ligne vierge requise au-dessus et au-dessous du bloc clôturé.
- Numéros de ligne : `` ```html {line-numbers="true"} ``
- Commencer la numérotation ailleurs : `` ```html {line-numbers="true" start-line="7"} ``
- Lignes de surbrillance : `` ```html {line-numbers="true" start-line="7" highlight="11-13, 16"} ``
- Le contenu du bloc de code n’est jamais localisé (à l’exception des balises `!UICONTROL`/`!DNL`, qui sont supprimées au moment de la publication).
- Aucune mise en forme Markdown/HTML (comme `<i>`) ne fonctionne dans les blocs de code : utilisez des crochets ou du texte brut pour les espaces réservés.

## Tableaux

- Les tables de tuyauterie GFM standard fonctionnent pour les cas simples.
- Les tableaux HTML sont autorisés dans des cas spéciaux (par exemple, un tableau sans ligne d’en-tête) ; préférez markdown dans le cas contraire.
- HTML limité est autorisé dans les cellules de tableau Markdown : `<p>`, `<br>`, `<ul>`, `<ol>`.
- Les tables peuvent être définies sur un rendu automatique ou fixe. Consultez l’article « Tables » lié au guide de syntaxe si vous avez besoin de ce niveau de contrôle.

## Sections réductibles

```markdown
+++See details

This is text inside a collapsible section.

* Bullet one
* Bullet two

+++
```

- N’imbriquez pas de sections réductibles : elles ne s’affichent pas correctement (et n’échouent pas lors de la validation, donc le bogue est envoyé silencieusement).
- Des lignes vides autour des listes internes/blocs de code à l’intérieur de la section sont requises, comme partout ailleurs.

## Mise en surbrillance du texte

```markdown
This sentence is normal. <span class="preview">This text is highlighted.</span>
```

Utilisez des `<span class="preview">` pour la mise en surbrillance des paragraphes/éléments intégrés, `<div class="preview">` pour plusieurs paragraphes/composants.

## Fragments de code et inclusions

- Ancres H2 partagées à partir du `help/snippets.md` d’un référentiel : référence avec `{{anchor-id}}`.
- Fichiers d’inclusion partagés depuis `help/_includes/*.md` : référencez avec `{{$include /help/_includes/filename.md}}`.

## Commentaires

```markdown
<!-- standard comment code -->
```

- N’utilisez jamais `<!--> bad comment syntax <-->` (tirets manquants) : le rendu est visible au lieu de masquer le texte.
- Les commentaires sont invisibles dans les documents rendus, mais **visibles par toute personne qui consulte le fichier .md brut sur GitHub**, sans secrets ni informations confidentielles.
- Évitez les commentaires dans les listes à puces (peut rompre le rendu de la liste). En `TOC.md`, commentez uniquement les lignes à la fin du fichier, jamais au milieu de la liste.

## Solution de contournement à ligne vierge

Les lignes vides supplémentaires dans la source sont réduites par le moteur de rendu. Pour forcer l&#39;espace vertical visible, placez le `<br>&nbsp;` sur sa propre ligne à l&#39;endroit où vous voulez que l&#39;espace soit supprimé.

## Caractères d’échappement

- Caractères pouvant être précédés d’une barre oblique inverse : `` # { } [ ] * + - . ! `` — par exemple `\# not a heading`.
- Pour les chevrons (`<placeholder>`), la barre oblique inverse ne fonctionne pas : utilisez un bloc de code intégré (`` `<placeholder>` ``) ou des entités HTML (`&lt;placeholder&gt;`).
- Les entités HTML à l’intérieur des blocs de code sont **pas** reconverties en caractère ; `&gt;` y conserve le texte littéral.
- Métadonnées (frontMATTER YAML) a ses propres règles d’échappement — si une valeur commence par un caractère spécial comme `:` ou `[`, citez la valeur entière : `title: "Processing rules: A new beginning"`.

## HTML restreinte à placer sur la liste autorisée

Seules ces balises HTML sont autorisées n’importe où dans Markdown ; toute autre balise est une erreur de validation :

```
table  tbody  td  tfoot  thead  th  tr  col  colgroup
p  ul  ol  li  br
b  i  strong  u  s  em  sub  sup  span
caption  a  img  div
pre  code  codeblock
```

Privilégiez la syntaxe Markdown à HTML lorsque Markdown peut effectuer le travail : HTML est réservé aux cas de périphérie, tels qu’un tableau sans en-tête.

## Explicitement non pris en charge (ne pas utiliser même si un aperçu local les effectue)

- Règles horizontales (`***`, `<hr>`)
- Emoji shortcodes (`:bowtie:`)
- Listes de tâches (`- [x] done`)
- Guillemet *composants* au-delà des codes courts note/onglet/vidéo (les guillemets simples `>` s’affichent sous la forme de guillemets, et non d’un composant stylisé)
- Syntaxe de la liste de définitions Markdown (utilisez plutôt le formatage manuel gras + tiret : `**Frog** - An amphibious green creature.`)
- `valign` sur les images

## Limites de taille de fichier/nombre à connaître

| Chose | Limite |
|---|---|
| Taille du fichier image/téléchargement | Avertissement de validation à 5 Mo, erreur à 20 Mo, limitation GitHub stricte à 100 Mo |
| Images par article | 100 (limite de rendu EDS) |
| Badges de métadonnées par article | 2 (par défaut) |
