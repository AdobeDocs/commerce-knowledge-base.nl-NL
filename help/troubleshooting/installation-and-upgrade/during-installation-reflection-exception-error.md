---
title: Fout tijdens installatie van Reflectie-uitzondering
description: Dit artikel biedt een oplossing voor de uitzonderingsfout Reflectie tijdens de installatie.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

Alle mappen en bestanden wissen onder Adobe Commerce `var` en installeer de Adobe Commerce-software opnieuw.

Als de [Adobe Commerce-eigenaar bestandssysteem](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) of als gebruiker met `root` Voer de volgende opdrachten in:

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
