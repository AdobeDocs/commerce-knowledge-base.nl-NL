---
title: Kan niet installeren met nginx
description: Dit artikel bevat een oplossing voor een mislukte Adobe Commerce-installatie bij gebruik van de nginx-webserver.
exl-id: 0af90c7e-0733-41c8-b217-9595b133fa95
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# Kan niet installeren met nginx

Dit artikel bevat een oplossing voor een mislukte Adobe Commerce-installatie bij gebruik van de nginx-webserver.

## Probleem

Als u de nginx-webserver gebruikt en de Adobe Commerce-software probeert te installeren, mislukt de installatie soms.

## Oplossing

U kunt het probleem bevestigen met de volgende fout in de map `var/report` :

```php
NOTE: You cannot install Adobe Commerce using the Setup Wizard because the Adobe Commerce setup directory cannot be accessed.
You can install Adobe Commerce using either the command line or you must restore access to the following directory: /var/www/html/setup
If you are using the sample nginx configuration, please go to http://ce.mtf03.bcn.magento.com/setup/";i:1;s:641:"#0 /var/www/html/lib/internal/Magento/Framework/App/Http.php(213): Magento\Framework\App\Http->redirectToSetup(Object(Magento\Framework\App\Bootstrap), Object(Exception))
```

### Workaround

Installeer de software van Adobe Commerce gebruikend de [&#x200B; bevellijn &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/advanced).
