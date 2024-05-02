---
title: '''"Updater application is not available"-fout'
description: Dit artikel spreekt over de oplossing voor de "updater toepassing is niet beschikbaar"kwestie u zou kunnen zien wanneer het proberen om Adobe Commerce op-gebouw bij te werken/te installeren gebruikend de Tovenaar van de Opstelling van het Web.
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Fout &quot;Updater application is not available&quot;

Dit artikel spreekt over de oplossing voor de &quot;updater toepassing is niet beschikbaar&quot;kwestie u zou kunnen zien wanneer het proberen om Adobe Commerce op-gebouw bij te werken/te installeren gebruikend de Tovenaar van de Opstelling van het Web.

## Probleem

Het volgende bericht wordt weergegeven bij de gereedheidscontrole:

![Screen_Shot_2019-08-29_at_1.39.12_PM.png](assets/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

## Betrokken producten/versies

* Adobe Commerce op locatie 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Oplossing

U kunt dit probleem oplossen door te kijken of er een `<magento_root>/update` map die bestanden en submappen bevat. Anders, zie [De updater instellen](https://devdocs.magento.com/guides/v2.3/comp-mgr/updater/update-updater.html) in onze ontwikkelaarsdocumentatie.
