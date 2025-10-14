---
title: Fout tijdens installatie van Reflectie-uitzondering
description: Dit artikel biedt een oplossing voor de uitzonderingsfout Reflectie tijdens de installatie.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Fout tijdens installatie van Reflectie-uitzondering

Dit artikel biedt een oplossing voor de uitzonderingsfout Reflectie tijdens de installatie.

## Details {#details}

Tijdens de installatie wordt een bericht weergegeven dat lijkt op het volgende:

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## Oplossing {#solution}

Wis alle mappen en bestanden onder de submap Adobe Commerce `var` en installeer de Adobe Commerce-software opnieuw.

Als [&#x200B; eigenaar van het het dossiersysteem van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) of als gebruiker met `root` voorrechten, ga de volgende bevelen in:

```bash
$ cd <your Magento install directory>/var
```

```bash
$ rm -rf var/cache/* di/* generation/* page_cache/*
```

### Redis {#redis}

Als u Redis gebruikt en nog steeds een fout krijgt, wist u de cache van Redis als volgt:

```bash
$ redis-cli FLUSHALL
```
