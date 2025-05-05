---
title: Tijdens de installatie worden onherstelbare BOB-foutmeldingen weergegeven
description: Dit artikel voorziet in een oplossing voor een uitzonderings fatale BOB-fout tijdens de installatie.
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Tijdens de installatie worden onherstelbare BOB-foutmeldingen weergegeven

Dit artikel voorziet in een oplossing voor een uitzonderings fatale BOB-fout tijdens de installatie.

## Probleem

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## Oplossing

Zorg ervoor u alle [ vereiste uitbreidingen PHP ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/php-settings) installeert.
