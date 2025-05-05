---
title: Fout bij plaatsen van volgorde met Authorize.net Sandbox-account (er is een fout opgetreden op de server)
description: Dit artikel bevat een correctie voor het foutbericht "*Er is een fout opgetreden op de server*" bij het plaatsen van een bestelling met Authorize.Net Direct Post.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Fout bij plaatsen van volgorde met Authorize.net Sandbox-account (er is een fout opgetreden op de server)

Dit artikel verstrekt een moeilijke situatie voor &quot;*een fout voorkwam op de server*&quot;foutenmelding wanneer het plaatsen van een orde gebruikend Authorize.Net Directe Post.

>[!WARNING]
>
>**Bericht van de Verdringing**
>
>Wegens de Richtlijn van de Dienst van de Betaling [ PSD2 ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive) en de voortdurende evolutie van vele APIs, is Authorize.Net het risico verouderd te worden en niet meer veiligheid volgzaam in de toekomst. Om deze reden, wordt het nu afgekeurd, en wij adviseren dat u het in uw configuratie van Adobe Commerce en overgang aan de overeenkomstige [ uitbreiding van de Commerce Marketplace ](https://marketplace.magento.com/extensions.html) onbruikbaar maakt.
>
>**Deze integratie wordt verwijderd uit Adobe Commerce 2.4.0 versie en is afgekeurd van de huidige versies van 2.3.**
>
>Voor details over het maken van een veilige overgang van verouderde betaalintegratie, zie onze [ DevBlog ](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Probleem

Het plaatsen van een orde gebruikend [ Authorize.Net de Directe rekening van de Post ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/error-placing-order-with-authorize-net-sandbox-account-an-error-occurred-on-the-server) Sandbox veroorzaakt een foutenmelding:

&#x200B;>>
&quot;Er is een fout opgetreden op de server. Probeer de bestelling opnieuw te plaatsen.&quot;

## Oorzaak 1: Testmodus is ingeschakeld

Het lijkt niet duidelijk, maar Authorize.net **het Testen Wijze** het plaatsen moet aan **Nr** worden geplaatst zelfs wanneer het testen met de rekening Sandbox.

## Oplossing 1: testmodus uitschakelen

1. Ga naar **Opslag** > **Configuratie** > **Verkoop** > **de Methoden van de Betaling** > **Andere Methoden van de Betaling** > **Authorize.net Directe Post**.
1. Plaats **Wijze van de Test** aan &quot;Nr&quot;(uncheck **systeemwaarde van het Gebruik**, dan uitgezochte &quot;Nr&quot;in het menu).
1. Klik **sparen Config**.

![ autorisze-net_test-mode_setting.png ](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Oorzaak 2: Onjuiste URL&#39;s

De instellingen Authorize.net bevatten mogelijk onjuiste URL-adressen voor de kritieke bronnen Authorize.Net.

## Oplossing 2: juiste URL&#39;s opgeven

* **Gateway URL:**   `https://test.authorize.net/gateway/transact.dll`
* **de Details URL van de transactie:**   `https://apitest.authorize.net/xml/v1/request.api`
* **API Verwijzing:**   `https://developer.authorize.net/api/reference/`

## Als niets geholpen heeft: krijg foutopsporingsinfo

Als het plaatsen van een orde met Authorize.net met een niet-informatieve *&quot;ging iets fout verkeerd&quot;* fout, controleer Adobe Commerce `debug.log`.

### Transact.dll

Voor het geval `debug.log` leeg is, controleer de **transact.dll** reactie in de console van uw Webbrowser:

1. Open de console.
1. Alvorens een orde te plaatsen, ga naar het **1&rbrace; lusje van het Netwerk en selecteer** Logboek **behouden.**    ![ web-console_network_preserve-log.png ](assets/web-console_network_preserve-log.png)
1. De reacties van de filter door **transact.dll** om een reactiebericht met een mogelijke fout te zien.    ![ transact-dll_web-console_response.png ](assets/transact-dll_web-console_response.png)
