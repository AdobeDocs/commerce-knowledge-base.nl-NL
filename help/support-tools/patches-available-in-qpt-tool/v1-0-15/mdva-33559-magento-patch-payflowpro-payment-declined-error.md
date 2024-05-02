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

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:** Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het probleem betreft het ampersand-teken (&amp;) en het gelijkteken (=) speciale tekens die in namen worden gebruikt.

<u>Stappen om te reproduceren</u>:

1. Voeg een eenvoudig product toe aan de wagen.
1. Ga naar Afrekenen.
1. Stel het verzendadres in. (Voorbeeld van verzendadres: **Voornaam** = ** *John* **  **Achternaam** = ** *Appels en sinaasappelen, Inc* **  **Adres** = *1234 E Naamloze St.*  **Land** = *VS*  **Staat/provincie** = *Anystate*  **Plaats** = *Anytown*  **Postcode** = *12345*  **Telefoon** = *1234567890*)
1. Betaling instellen op **PayPal PayflowPro** en probeer het afrekenen te voltooien.

<u>Verwachte resultaten</u>:

De transactie resulteert in een geslaagde betaling of een correct foutbericht, zoals u had verwacht.

<u>Werkelijke resultaten</u>:

De transactie wordt geweigerd en de klant ontvangt een e-mail met de tekst &quot;Transactie is geweigerd&quot;.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
