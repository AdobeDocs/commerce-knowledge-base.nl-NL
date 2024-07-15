---
title: 'MDVA-33559 patch: PayflowPro payment failed error'
description: De patch MDVA-33559 lost het probleem op waarbij PayPal PayflowPro-betalingen worden geweigerd.
exl-id: aec57ffa-07c7-404e-985d-8ec4fdb019b1
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# MDVA-33559 patch: PayflowPro-betaling afgewezen fout

De patch MDVA-33559 lost het probleem op waarbij PayPal PayflowPro-betalingen worden geweigerd.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur en Adobe Commerce op-gebouw 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het probleem betreft het ampersand-teken (&amp;) en het gelijkteken (=) speciale tekens die in namen worden gebruikt.

<u> Stappen om </u> te reproduceren:

1. Voeg een eenvoudig product toe aan de wagen.
1. Ga naar Afrekenen.
1. Stel het verzendadres in. (Voorbeeld verschepend adres: **Voornaam** = ** *John&#39;s* ** **Familienaam** = ** *Apples &amp; Orange, Inc* ** **Adres van de Straat** = *1234 E Nameless* **Land** = *US* **Staat/Provincie** = *om het even welke Staat* **Stad** = *om het even welk* **Zip** = *12345* **Telefoon** = *1234567890*)
1. Plaats betaling aan **PayPal PayflowPro** en probeer om uitbetaling te voltooien.

<u> Verwachte resultaten </u>:

De transactie resulteert in een geslaagde betaling of een correct foutbericht, zoals u had verwacht.

<u> Ware resultaten </u>:

De transactie wordt geweigerd en de klant ontvangt een e-mail met de tekst &quot;Transactie is geweigerd&quot;.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
