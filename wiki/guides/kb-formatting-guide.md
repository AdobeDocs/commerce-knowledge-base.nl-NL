---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---
# KB-opmaakgids

## Auteur in markeringen

Over het algemeen, gebruiken wij [ Gids van de Stijl van de Syntaxis van de Markering van Adobe Experience League ](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=en), maar er zijn sommige verschillen en uitzonderingen. Bovendien zijn bepaalde HTML-tags in bepaalde gevallen vereist.

Hier volgen voorbeelden van de opmaak Markering die het meest wordt gebruikt in onze reactie.

## Basisopmaak

Als u tekst vet wilt opmaken, plaatst u de tekst in twee sterretjes:

`This will be **bold** text`

Als u tekst wilt opmaken als cursief, gebruikt u één sterretje:

`This text will be *italics*`

Als u tekst wilt opmaken als onderstreept, gebruikt u de tag `<ins>` :

`<ins>This text will be underlined</ins>`

Als u een regeleinde wilt toevoegen, gebruikt u de tag `<br>` HTML.


## Kopteksten

Gebruik de volgende opmaak voor kopteksten van H2 tot en met H5. H1 wordt nooit gebruikt omdat de titel van het artikel als H1 wordt beschouwd.

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## Inline code en blokken

Gebruik enkele backtiks om het code-element te omsluiten dat u wilt markeren:

Dit is \&quot;inline code\&quot; in een alinea tekst.

### Codeblokken

Als u een codeblok wilt invoegen, plaatst u het codeblok in drievoudige achtergronden en geeft u de taal op na het openen van drievoudige achtergronden:

\``\`\` sql

SELECT TABLE_NAME AS `Table` ,
ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = &quot;%project_id%&quot;
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;

\``\` `\`

Dit wordt weergegeven als:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Volgens onze regels voor het koppelen moet u altijd een taal voor het codeblok opgeven.

Ga naar https://github.com/github/linguist/blob/master/lib/linguist/languages.yml voor de lijst met ondersteunde talen.

Als de markering niet werkt voor een bepaalde taal in de markering (de taal wordt dus niet ondersteund), gebruikt u de volgende HTML als u deze ten minste wilt markeren bij publicatie naar https://support.magento.com/hc/en-us/:

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

Waar ``%language-code%`` de codes zijn die door [ worden bepaald Prism.js gesteunde talen ](https://prismjs.com/#supported-languages).

## Lijsten

Lijsten altijd van de rest van inhoud scheiden door lege regels. Lijsten moeten worden voorafgegaan en gevolgd door een lege regel.

Gebruik de volgende opmaak voor geordende lijsten:

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

Als u een niet-geordende lijst met opsommingstekens wilt maken, begint u met een regel met *, of + of -. Maar selecteer één methode en gebruik deze consistent in het hele artikel.

Voorbeeld:

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

Als u inhoud wilt toevoegen tussen lijstitems, voegt u 4 spaties toe aan het begin van de regel:

```markdown
* List item.
* List item.
    Here's some content between list items.
* Here we continue the list
```

U kunt lijsten ook op deze manier insluiten.

## Koppelingen

Externe koppelingen zijn eenvoudig:

```markdown
[Adobe](https://www.adobe.com)
```

### Koppelingen naar bijlagen

Elke bijlage moet de indelingen .png, .jpg en .jpeg hebben. Voor veiligheidsdoeleinden accepteren we alleen bijlagen in een van de drie indelingen.

Om een beeld op te nemen, plaats het beeld aan *activa* subfolder in de zelfde sectieomslag zoals het artikel, en gebruik de volgende syntaxis om het beeld aan uw artikel op te nemen:

```markdown
![alt text](assets/image.png)
```

Als u de grootte van de afbeelding wilt aanpassen, moet u dat doen met de volgende HTML-tag:

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### Koppelingen naar specifieke secties in het artikel

Als u naar een sectie in uw artikel moet verwijzen, hoeft u geen afzonderlijk anker te maken. Deze worden automatisch tijdens de publicatie voor alle H2-H6-koppen gegenereerd. De ankers worden gegenereerd op basis van de koptekst door alle woorden in kleine letters te maken en &quot;-&quot; te gebruiken voor het scheiden van woorden.

Voorbeeld:

```markdown
## This is header
```

Dit is een koppeling naar deze header:

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

Als u een element buiten kopbal moet van verwijzingen voorzien, gebruik HTML om het element te bepalen om het [ attribuut van identiteitskaart ](https://www.w3schools.com/html/html_id.asp) toe te voegen. Vervolgens kunt u Markdown of HTML gebruiken om naar deze ID te verwijzen.

### Relatieve koppelingen en koppelingen naar andere artikelen

Gebruik geen relatieve koppelingen om te verwijzen naar onze artikelen in de basis van supportkennis. Die verbindingen zullen niet werken wanneer uw artikel in het [ Centrum van de Hulp van Adobe Commerce ](https://support.magento.com/hc/en-us) wordt gepubliceerd.
Gelieve te gebruiken volledige hyperlinks van het [ Centrum van de Hulp van Adobe Commerce ](https://support.magento.com/hc/en-us).


## Tabellen

Gebruik [ HTML het formatteren voor lijsten ](https://www.w3schools.com/html/html_tables.asp).


## Waarschuwingen en infoblokken

Blok succesvolle notitie:

```
>![success]
>
>This is a success note
```

Waarschuwingsblok:

```
>![warning]
>
>This is a warning
```

Blok Info notitie:

```
>![info]
>
>This is a block with additional info
```
