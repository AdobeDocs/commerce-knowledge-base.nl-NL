---
title: "MDVA-31295: Loyalty points on partiële orders"
description: De patch MDVA-31295 verhelpt het probleem dat bonuspunten niet correct worden berekend wanneer een gedeeltelijke bestelling wordt voltooid en items worden belast. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 10e8a3a9-bfab-4256-b772-fd64e8885da3
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31295: Loyalty-punten op gedeeltelijke bestellingen

De patch MDVA-31295 verhelpt het probleem dat bonuspunten niet correct worden berekend wanneer een gedeeltelijke bestelling wordt voltooid en items worden belast. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce op locatie 2.3.0

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Rentelasten worden niet toegepast op de rekeningen van de klant wanneer de bestelling volledig is (gedeeltelijk verzonden) en objecten worden belast. Wanneer de items niet worden belast, worden de beloningen met succes toegevoegd aan de accounts van de klanten.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de winkel als klant.
1. Voeg twee producten aan de kar toe.
1. Ga naar de afhandeling, stel het verzendadres in waarop belasting wordt geheven en plaats de bestelling.
1. Ga in de beheerder naar de onlangs geplaatste volgorde.
1. Klikken **Factuur** en instellen **Aantal op factuur** tot 0 voor een van de items en klik op **Aantal bijwerken**. Factuur verzenden.
1. Klik op Verzenden en stel deze in **Aantal naar verzending** tot 0 voor het object dat niet is gefactureerd. Klikken **Verzending verzenden**.
1. Klik op Volgorde annuleren. De status wordt ingesteld op Voltooid.
1. Ga in de beheerder naar **Klanten** > Kies een klant die aanschaft voor > **Punten omkeren** > **Geschiedenis van terugkeringspunten**.
1. Controleer de verdiende bonuspunten voor de geplaatste order.

<u>Verwachte resultaten</u>:

De beloningspunten moeten worden berekend voor belastbare orders wanneer een gedeeltelijke order is voltooid.

<u>Werkelijke resultaten</u>:

Retourpunten worden niet berekend voor een belastbare order wanneer een gedeeltelijke order is voltooid.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
