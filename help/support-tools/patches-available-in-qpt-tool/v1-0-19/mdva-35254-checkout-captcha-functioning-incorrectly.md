---
title: "MDVA-35254: Uitchecken CAPTCHA functioneert onjuist"
description: De patch MDVA-35254 verhelpt het probleem met CAPTCHA-velden die niet worden weergegeven na een ongeslaagd aantal pogingen tot afhandeling voor betaling door derden. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35254. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: 226c672b-3740-4a87-9ea1-66892acb9fe2
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-35254: Uitchecken CAPTCHA functioneert onjuist

De patch MDVA-35254 verhelpt het probleem met CAPTCHA-velden die niet worden weergegeven na een ongeslaagd aantal pogingen tot afhandeling voor betaling door derden. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35254. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.1-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

CAPTCHA configureren:

1. Een andere betalingsprovider installeren en configureren (bijvoorbeeld Braintree).
1. Ga naar **Store > Configuration > Customer > Customer Configuration > CAPTCHA > Forms**.
1. Selecteren **Afhandeling/Plaatsingsvolgorde**.
1. Houd de **Aantal mislukte aanmeldpogingen** as default (default = *3*).
1. Meld u aan als klant.
1. Voeg een product toe aan het winkelwagentje.
1. Ga naar het betalingsgedeelte bij de afhandeling.
1. Selecteren **Creditcard** betalingsmethode (voorbeeld: Braintree).
1. Voer drie mislukte betalingspogingen uit.

<u>Verwachte resultaten</u>:

Het veld CAPTCHA wordt weergegeven wanneer het aantal mislukte pogingen is bereikt.

<u>Werkelijke resultaten</u>:

Het veld CAPTCHA wordt nooit weergegeven, alleen het foutbericht: *Geef de CAPTCHA-code op en probeer het opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
