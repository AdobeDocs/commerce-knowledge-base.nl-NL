---
title: "MDVA-42645: Admin kan geen bonuspunten terugbetalen voor een creditering van een gehandicapte winkel"
description: De MDVA-42645-patch lost het probleem op waarbij de beheerder geen bonuspunten kan terugbetalen als de functionaliteit voor winkelkrediet is uitgeschakeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-42645. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 8e8f8c07-c1a2-4031-a2fb-cb737165dc2c
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-42645: Admin kan geen bonuspunten terugbetalen voor creditering van winkels met een handicap

De MDVA-42645-patch lost het probleem op waarbij de beheerder geen bonuspunten kan terugbetalen als de functionaliteit voor winkelkrediet is uitgeschakeld. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-42645. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De beheerder kan geen bonuspunten terugbetalen als de functionaliteit voor winkelkrediet is uitgeschakeld.

<u>Stappen om te reproduceren</u>:

1. Maak een eenvoudig product.
1. Maak een nieuwe klantenaccount en voeg wat bonuspunten toe.
1. Schakel de functie Winkelkrediet uit door naar **Winkel** > Instellingen > **Configuratie** > **Klant** > **Klantconfiguratie** > **Crediteringsopties voor winkel**.
1. Meld u aan als de klant aan wie de bonuspunten zijn toegewezen.
1. Voeg een product toe aan de winkelwagentje en navigeer naar de kassa.
1. Gebruik de bonuspunten in de betalingssectie en plaats de bestelling.
1. Open de bestelling in de beheerder en factureer de bestelling.
1. Klik op de knop **Kredietfaciliteit** link om een nieuwe creditnota te maken.
1. Tik op de optie Punten voor terugbetaling naar achteren onderaan en klik op de knop **Offline terugbetalen**.

<u>Verwachte resultaten</u>:

* Het creditmemo is gemaakt.
* De bonuspunten worden met succes terugbetaald.

<u>Werkelijke resultaten</u>:

U krijgt het volgende foutbericht: *Je kunt geen creditering gebruiken die hoger is dan het orderbedrag.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
