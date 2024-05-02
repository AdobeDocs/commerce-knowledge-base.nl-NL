---
title: Fout bij plaatsen van volgorde met Authorize.net Sandbox-account (er is een fout opgetreden op de server)
description: Dit artikel bevat een correctie voor het foutbericht "*Er is een fout opgetreden op de server*" bij het plaatsen van een bestelling met Authorize.Net Direct Post.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Fout bij plaatsen van volgorde met Authorize.net Sandbox-account (er is een fout opgetreden op de server)

Dit artikel bevat een oplossing voor &quot;*Er is een fout opgetreden op de server*&quot;foutbericht bij het plaatsen van een bestelling met Authorize.Net Direct Post.

>[!WARNING]
>
>**Kennisgeving van veroudering**
>
>Als gevolg van de Richtlijn Betalingsdiensten [PSD 2](https://docs.magento.com/user-guide/v2.3/stores/compliance-payment-services-directive.html) en de voortdurende evolutie van vele APIs, Authorize.Net loopt het risico verouderd te worden en niet meer veiligheids volgzaam in de toekomst. Daarom is deze nu afgekeurd en raden we u aan deze optie uit te schakelen in uw Adobe Commerce-configuratie en over te schakelen naar de bijbehorende [Commerce Marketplace-uitbreiding](https://marketplace.magento.com/extensions.html).
>
>**Deze integratie is verwijderd uit de Adobe Commerce 2.4.0-versie en is vervangen door de huidige versie van 2.3.**
>
>Voor meer informatie over het maken van een veilige overgang van verouderde integratie in de betalingssector raadpleegt u onze [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Probleem

Een bestelling plaatsen met [Autoriseren.Net Direct Post](https://docs.magento.com/user-guide/v2.3/payment/authorize-net-direct-post.html) Sandbox-account veroorzaakt een foutbericht:

>>
&quot;Er is een fout opgetreden op de server. Probeer de bestelling opnieuw te plaatsen.&quot;

## Oorzaak 1: Testmodus is ingeschakeld

Het lijkt niet vanzelfsprekend, maar het bestand Authorize.net **Testmodus** instellen op **Nee** zelfs bij het testen met de account Sandbox.

## Oplossing 1: testmodus uitschakelen

1. Ga naar **Winkels** > **Configuratie** > **Verkoop** > **Betalingsmethoden** > **Andere betalingsmethoden** > **Authorize.net Direct Post**.
1. Set **Testmodus** naar &quot;Nee&quot; (uitschakelen **Systeemwaarde gebruiken** en selecteert u vervolgens &quot;Nee&quot; in het menu).
1. Klikken **Config opslaan**.

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Oorzaak 2: Onjuiste URL&#39;s

De instellingen Authorize.net bevatten mogelijk onjuiste URL-adressen voor de kritieke bronnen Authorize.Net.

## Oplossing 2: juiste URL&#39;s opgeven

* **Gateway-URL:**   `https://test.authorize.net/gateway/transact.dll`
* **Transactiedetails-URL:**   `https://apitest.authorize.net/xml/v1/request.api`
* **API-referentie:**   `https://developer.authorize.net/api/reference/`

## Als niets geholpen heeft: krijg foutopsporingsinfo

Als het plaatsen van een orde met Authorize.net ontbreekt met niet-informatief *&quot;Er is iets fout gegaan&quot;* fout, controleer de Adobe Commerce `debug.log`.

### Transact.dll

In het geval van `debug.log` is leeg, controleer **transform.dll** reactie in de console van uw webbrowser:

1. Open de console.
1. Voordat u een bestelling plaatst, gaat u naar de **Netwerk** en selecteert u **Logbestand behouden**.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Reacties filteren op **transform.dll** om een antwoordbericht met een mogelijke fout te zien.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
