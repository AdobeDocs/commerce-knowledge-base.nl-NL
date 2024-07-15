---
title: Bekende kwesties die xdebug installatie beïnvloeden
description: Dit artikel biedt een oplossing voor het gebruik van de optionele PHP extensie ` xdebug` als je een uitzonderingsfout ervaart.
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Bekende kwesties die xdebug installatie beïnvloeden

Dit artikel biedt een oplossing voor het gebruik van de optionele PHP extensie `xdebug` als er een uitzonderingsfout optreedt.

* Tijdens de installatie
* Toegang verkrijgen tot Commerce Admin of storefront na een geslaagde installatie

Voorbeelduitzondering:

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

U kunt dit probleem als volgt oplossen:

* Schakel de extensie `xdebug` uit.
* Stel de waarde van `xdebug.max_nesting_level` in op een waarde van 200 of meer. Voor meer informatie, zie [ xdebug documentatie ](http://xdebug.org/docs/basic#max_nesting_level).

Nadat u de configuratie van `xdebug` hebt gewijzigd of uitgeschakeld, start u Apache opnieuw:

* CentOS: `sudo service httpd restart`
* Ubuntu: `sudo service apache2 restart`
