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

De patch MDVA-31295 verhelpt het probleem dat bonuspunten niet correct worden berekend wanneer een gedeeltelijke bestelling wordt voltooid en items worden belast. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce op locatie 2.3.0

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Rentelasten worden niet toegepast op de rekeningen van de klant wanneer de bestelling volledig is (gedeeltelijk verzonden) en objecten worden belast. Wanneer de items niet worden belast, worden de beloningen met succes toegevoegd aan de accounts van de klanten.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de winkel als klant.
1. Voeg twee producten aan de kar toe.
1. Ga naar de afhandeling, stel het verzendadres in waarop belasting wordt geheven en plaats de bestelling.
1. Ga in de beheerder naar de onlangs geplaatste volgorde.
1. Klik **Factuur** en plaats **Aantal aan Factuur** aan 0 voor één van de punten, en klik **Aantal van de Update**. Factuur verzenden.
1. Klik Schip en plaats **Aantal aan Schip** aan 0 voor het punt dat niet werd gefactureerd. Klik **voorleggen Verzending**.
1. Klik op Volgorde annuleren. De status wordt ingesteld op Voltooid.
1. In admin, ga naar **Klanten** > kiezen klantenaankoop die vóór > **wordt gemaakt Punten** > **teruggeeft de Geschiedenis van Punten**.
1. Controleer de verdiende bonuspunten voor de geplaatste order.

<u> Verwachte resultaten </u>:

De beloningspunten moeten worden berekend voor belastbare orders wanneer een gedeeltelijke order is voltooid.

<u> Ware resultaten </u>:

Retourpunten worden niet berekend voor een belastbare order wanneer een gedeeltelijke order is voltooid.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
