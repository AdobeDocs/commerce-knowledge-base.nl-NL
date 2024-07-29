---
title: git pull origin develop failed when update the Adobe Commerce software
description: Dit artikel biedt een oplossing voor het geval dat u geen Adobe Commerce-software kunt bijwerken wanneer 'git pull origin develop' wordt uitgevoerd.
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# git pull origin develop failed when update the Adobe Commerce software

Dit artikel biedt een oplossing voor het probleem wanneer u geen Adobe Commerce-software kunt bijwerken wanneer `git pull origin develop` wordt uitgevoerd.

## Details

Een van de stappen voor het bijwerken van de Adobe Commerce-software is het bijwerken van uw lokale opslagplaats door het uitvoeren van:

```bash
$ git pull origin develop
```

De volgende fout kan worden weergegeven:

```bash
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

Als u wilt weten welke bestanden moeten worden overschreven, leest u het bericht of voert u in:

```bash
git status
```

In de volgende sectie worden de voorgestelde oplossingen besproken.

### Voorgestelde oplossingen

Uw oplossing hangt af van het feit of u opzettelijk bestanden hebt gewijzigd in het Adobe Commerce-bestandssysteem. Zie een van de volgende secties voor meer informatie.

#### U hebt bestanden met opzet gewijzigd

Los de conflicten handmatig op de gebruikelijke manier op. Als u niet zeker bent wat te doen, raadpleeg [ hulp GitHub ](https://help.github.com/).

#### Bestanden zijn niet opzettelijk gewijzigd

Probeer een van de volgende handelingen uit:

* Als u zeker weet dat u geen bestanden hebt gewijzigd en u de wijzigingen in het Adobe Commerce-bestandssysteem niet wilt verwijderen of overschrijven, voert u het volgende in:

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  Ga vervolgens verder waar je bent gebleven met je Adobe Commerce-update.

* Het is mogelijk dat een configuratie GitHub het plaatsen deze fouten in de toekomst kan verhinderen. Door gebrek, slaat GitHub inhoud op gebruikend het werkende systeem-gebrek lijn beëindigende karakters. Als u Linux gebruikt, maar een andere medewerker een verandering gebruikend Vensters toewees, zet GitHub de de lijneindingen van Vensters in Linux om wanneer u kloont of trekt. Hierdoor lijkt het alsof bestanden zijn gewijzigd, terwijl er in feite geen wijziging is aangebracht.

  Om GitHub te vormen om lijneinden te negeren, ga het volgende bevel in uw cliënt van het Git in:

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  Als u Windows gebruikt, voert u het volgende in:

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >De Adobe adviseert of bevestigt geen bepaalde GitHub configuratiemontages. Het voorgaande is alleen suggesties. Voor meer informatie, raadpleeg [ hulp GitHub ](https://help.github.com/).

  Ga door waar je bent gebleven met je Adobe Commerce-update.
