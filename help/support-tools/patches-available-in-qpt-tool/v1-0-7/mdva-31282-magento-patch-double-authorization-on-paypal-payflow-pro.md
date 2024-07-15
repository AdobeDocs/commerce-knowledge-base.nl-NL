---
title: 'MDVA-31282: dubbele autorisatie op Paypal PayFlow Pro'
description: De MDVA-31282-patch lost het probleem op wanneer er dubbele autorisaties plaatsvinden op Paypal PayFlow Pro in Adobe Commerce. De dubbele autorisaties hebben ook tot gevolg dat de frauduleuze filters van PayFlow Pro worden overgeslagen en dat transactiekosten worden verdubbeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd.
exl-id: f239012e-e1bd-474b-aad2-7218ec3a3d1b
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31282: dubbele vergunning voor Paypal PayFlow Pro

De MDVA-31282-patch lost het probleem op wanneer er dubbele autorisaties plaatsvinden op Paypal PayFlow Pro in Adobe Commerce. De dubbele autorisaties hebben ook tot gevolg dat de frauduleuze filters van PayFlow Pro worden overgeslagen en dat transactiekosten worden verdubbeld. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 geïnstalleerd is.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.3.3 en 2.3.5 - 2.3.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er zijn dubbele autorisaties in PayPal PayFlow Pro in Adobe Commerce die tot gevolg hebben dat de fraudefilters van PayFlow Pro worden overgeslagen en transactiekosten worden verdubbeld.

<u> Eerste vereisten </u>:

Configureer PayPal PayFlow Pro-betalingsmethode.

<u> Stappen om </u> te reproduceren:

1. Ga naar de frontend als gastklant.
1. Voeg producten aan **het Winkelen Kart** van productpagina&#39;s toe.
1. Ga aan **Controle** te werk.
1. Specificeer **Verzendadres** als adres in Land \#1 (Voorbeeld: adres van het VK), en selecteer een het verschepen methode.
1. Selecteer **PayPal PayFlow Pro** als betalingsmethode. Specificeer het **Facturerings adres** als adres in Land \#2 (Voorbeeld: adres van de V.S.).
1. Voer creditcardgegevens in en plaats de bestelling.
1. Navigeer aan **Verkoop** > **Orders** in admin en neem gecreeerde orde waar.

<u> Verwachte resultaten </u>:

* Het blok van de Informatie van de Betaling toont: *&quot;teweeggebrachte Fraudefilters: RESPMSG: onder overzicht door de Dienst van de Fraude*. *de Orde is in Vermoedelijke Fraudestatus&quot;*.
* PayPal Pro toont één transactie voor autorisatie zoals verwacht.

<u> Ware resultaten </u>:

* Het blok van de Informatie van de Betaling toont: *&quot;teweeggebrachte Fraudefilters: RESPMSG: onder overzicht door de Dienst van de Fraude*. *de Orde is in de status van de Verwerking&quot;*.
* PayPal Pro toont dubbele autorisatietransacties.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
