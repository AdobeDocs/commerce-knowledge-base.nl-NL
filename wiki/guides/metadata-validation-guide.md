---
source-git-commit: 0cfb7dc0dce68bcb0933a5ae49b0cd5a8b5b5a39
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---
# Handleiding voor metagegevensvalidatie

Voor een correcte opmaak van metagegevens in MD-bestanden hebben we een validatietest voor metagegevens ingesteld. Dit document bevat richtlijnen die contribuanten helpen enkele van de meest voorkomende validatiefouten voor metagegevens te voorkomen.

**Voorbeeld van metagegevens:**

```markdown
---
title: This is a title
labels: article,labels,tags
---

Article content...
```

## Algemene validatiefouten en hoe deze te voorkomen/te herstellen

Hieronder vindt u een aantal van de meest voorkomende scenario&#39;s waarin validatiefouten voor metagegevens optreden.

### Colon in metagegevens

Er treedt een validatiefout op als de titel of labels of beide dubbele punten bevatten.

**Voorbeeld:**

```markdown
---
title: Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,article,labels,tags
---
```

U voorkomt deze fout door de titel of labels (of beide als ze dubbele punten hebben) te plaatsen in **enkele aanhalingstekens**.

**Voorbeeld:**

```markdown
---
title: 'Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure'
labels: 'patch: 2041.1,article,labels,tags'
---
```

### Colon en enkel aanhalingsteken of apostrof in meta-gegevens

De vorige oplossing werkt niet als de titel of labels dubbele punten, enkele aanhalingstekens of apostroffen bevatten.

**Voorbeeld:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,'article',labels,tags
---
```

Deze fout is opgelost door de titel of de labels (of beide) in te sluiten **dubbele aanhalingstekens**.

**Voorbeeld:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure"
labels: "patch: 2041.1,'article',labels,tags"
---
```

### Dubbele punt, dubbel aanhalingsteken en enkel aanhalingsteken of apostrof in metagegevens

**Voorbeeld:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe "Commerce" on cloud infrastructure
labels: patch: 2041.1,'article',"labels",can't,tags
---
```

Wanneer dit gebeurt, plaatst u de titel of labels (of beide) in **dubbele aanhalingstekens** en gebruiken een **backslash** om alle dubbele aanhalingstekens in de titel en de labels te verwijderen.

**Voorbeeld:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe \"Commerce\" on cloud infrastructure"
labels: "patch: 2041.1,'article',\"labels\",can't,tags"
---
```

### Ontbrekende velden in metagegevens

Er treedt een validatiefout op als het veld Titel of het veld Labels in de metagegevens ontbreekt.

**Voorbeeld:**

```markdown
---
title: This is a title
---
```

OF

```markdown
---
labels: article,labels,tags
---
```

Als u deze fout wilt voorkomen, neemt u beide velden op in de metagegevens.

Het veld Labels kan leeg worden gelaten en dit leidt niet tot een fout, maar het veld Titel moet wel worden ingevuld.

**Voorbeeld:**

```markdown
---
title: Unlike labels the title field must be filled
labels:
---
```
