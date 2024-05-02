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

De MDVA-31282-patch lost het probleem op wanneer er dubbele autorisaties plaatsvinden op Paypal PayFlow Pro in Adobe Commerce. De dubbele autorisaties hebben ook tot gevolg dat de frauduleuze filters van PayFlow Pro worden overgeslagen en dat transactiekosten worden verdubbeld. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.3.3 en 2.3.5 - 2.3.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er zijn dubbele autorisaties in PayPal PayFlow Pro in Adobe Commerce die tot gevolg hebben dat de fraudefilters van PayFlow Pro worden overgeslagen en transactiekosten worden verdubbeld.

<u>Vereisten</u>:

Configureer PayPal PayFlow Pro-betalingsmethode.

<u>Stappen om te reproduceren</u>:

1. Ga naar de frontend als gastklant.
1. Producten toevoegen aan **Winkelwagentje** van productpagina&#39;s.
1. Doorgaan naar **Afhandeling**.
1. Opgeven **Verzendadres** als een adres in Land \#1 (Voorbeeld: adres in het Verenigd Koninkrijk) en selecteer een verzendmethode.
1. Selecteren **PayPal PayFlow Pro** als betalingsmethode. Geef de **Factuuradres** als een adres in Land \#2 (Voorbeeld: adres VS).
1. Voer creditcardgegevens in en plaats de bestelling.
1. Navigeren naar **Verkoop** > **Orders** in beheer en neemt de gemaakte volgorde in acht.

<u>Verwachte resultaten</u>:

* In het vak Betalingsinformatie wordt het volgende weergegeven: *&quot;Teweeggebrachte fraude filters: RESPMSG: onder controle door de Fraud Service*. *De bestelling heeft de status Verdacht fraude&quot;*.
* PayPal Pro toont één transactie voor autorisatie zoals verwacht.

<u>Werkelijke resultaten</u>:

* In het vak Betalingsinformatie wordt het volgende weergegeven: *&quot;Teweeggebrachte fraude filters: RESPMSG: onder controle door de Fraud Service*. *De bestelling bevindt zich in de verwerkingsstatus.&quot;*.
* PayPal Pro toont dubbele autorisatietransacties.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
