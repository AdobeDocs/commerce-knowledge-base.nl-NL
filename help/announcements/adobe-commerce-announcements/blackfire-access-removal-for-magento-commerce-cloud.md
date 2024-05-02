---
title: Blackfire access removal voor Adobe Commerce op cloudinfrastructuur
description: Op 11 april 2020 zal de gratis toegang tot prestatiebewaking voor Blackfires niet langer worden opgenomen in Adobe Commerce op de architectuur van het Pro-plan voor cloudinfrastructuur of in Adobe Commerce op de abonnementsabonnementen van de Starter-architectuur voor de startarchitectuur van de cloud-infrastructuur.  U kunt zich niet meer aanmelden bij uw Blackfire-account. Het is mogelijk om Blackfire na 11 april te blijven gebruiken door een licentie rechtstreeks aan te schaffen via Blackfire.io. Adobe Commerce-handelaren die op die datum geen licenties rechtstreeks bij Blackfire hebben gekocht, zullen hun gratis, door Adobe verschafte Blackfire-licenties laten deactiveren. Daarnaast wordt de functionaliteit voor het maken van nieuwe rapporten met het gereedschap Profiler uitgeschakeld. Klanten die gebruikmaken van Pro-architectuur die wordt gehost op cloudinfrastructuur, kunnen via New Relic Infrastructure nog steeds gratis toezicht op de infrastructuurprestaties krijgen.
exl-id: bf33c2c6-e9b3-474a-a127-909b51dff92f
feature: Cloud, Paas
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Blackfire access removal voor Adobe Commerce op cloudinfrastructuur

Op 11 april 2020 zal de gratis toegang tot prestatiebewaking voor Blackfires niet langer worden opgenomen in Adobe Commerce op de architectuur van het Pro-plan voor cloudinfrastructuur of in Adobe Commerce op de abonnementsabonnementen van de Starter-architectuur voor de startarchitectuur van de cloud-infrastructuur.  U kunt zich niet meer aanmelden bij uw Blackfire-account. Het is mogelijk om Blackfire na 11 april te blijven gebruiken door een licentie rechtstreeks aan te schaffen via Blackfire.io. Adobe Commerce-handelaren die op die datum geen licenties rechtstreeks bij Blackfire hebben gekocht, zullen hun gratis, door Adobe verschafte Blackfire-licenties laten deactiveren. Daarnaast wordt de functionaliteit voor het maken van nieuwe rapporten met het gereedschap Profiler uitgeschakeld. Klanten die gebruikmaken van Pro-architectuur die wordt gehost op cloudinfrastructuur, kunnen via New Relic Infrastructure nog steeds gratis toezicht op de infrastructuurprestaties krijgen.

**Als u Blackfire wilt blijven gebruiken**:

1. U moet een licentie rechtstreeks bij Blackfire aanschaffen.
1. Stel vervolgens de Blackfire in met deze [stappen](https://blackfire.io/docs/integrations/paas/magentocloud).
1. Als u problemen ondervindt met de installatie, kunt u [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om bijstand te verzoeken. Voor specifieke vragen over Blackfire kunt u rechtstreeks contact opnemen met de Blackfire op [support@blackfire.io](mailto:support@blackfire.io).

## Als u fouten hebt bij het uitvoeren van een implementatie:

Als wanneer het runnen van een plaatsing u Blackfire verwante fouten krijgt doe het volgende:

1. Verwijder Blackfire uit uw configuratie. Bewerk de `.magento.app.yaml` bestand en Blackfire verwijderen uit de runtime-sectie:

   ```YAML
   ...
   # Enable extensions required by Magento 2
   runtime:
     extensions:
     - redis
     - xsl
     - json
     -**blackfire**
      - imap
   ...
   ```

1. Voltooi dit op de Lokale ontwikkelomgeving en duw omhoog aan de wolk.

Alleen [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) als u de volgende fout ziet nadat u een plaatsing in werking stelt:

*PHP Waarschuwing: PHP Startup: Unable load dynamic library &#39;blackfire.so&#39; (probeerde: /usr/lib/php/20180731-zts/blackfire.so (/usr/lib/php/20180731-zts/blackfire.so: cannot open shared object file: No such file or directory), /usr/lib/php/20180731-zts/blackfire.so.so (/usr/lib/php/20180731-zts/blackfire.so.so: cannot open shared object file: No such file or directory) in Unknown on line 0*

Deze fout houdt in dat de insteekmodule Blackfire moet worden bijgewerkt en dat het laden ervan moet worden gestopt.

**Als u New Relic Infrastructure wilt gebruiken**:

Ga voor meer informatie over toegang tot New Relic Infrastructure naar [Toegang tot New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) in onze kennisbasis voor ondersteuning.
