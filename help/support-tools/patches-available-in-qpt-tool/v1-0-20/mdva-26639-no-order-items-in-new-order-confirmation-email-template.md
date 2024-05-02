---
title: 'MDVA-26639: geen bestelling-items in nieuwe e-mailsjabloon voor bevestiging van bestelling'
description: De patch MDVA-26639 verhelpt het probleem bij het maken van een nieuwe bestelling. De bestellingspunten ontbreken in een bevestigings-e-mailsjabloon.
exl-id: 5d9716ab-6e57-47b0-8b38-ca98a98101e8
feature: Communications, Marketing Tools, Native Luma Frontend Development, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# MDVA-26639: geen bestelling-items in e-mailsjabloon voor bevestiging van nieuwe bestelling

De patch MDVA-26639 verhelpt het probleem bij het maken van een nieuwe bestelling. De bestellingspunten ontbreken in een bevestigings-e-mailsjabloon.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-26639. De kwestie is opgelost in Adobe Commerce 2.3.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.3.3-p1

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.3-p1-2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > **Configuratie** > **Verkoop** > **Verkoop-e-mails** > **Bevestiging van nieuwe bestelling** en selecteert u **Sjabloon: nieuwe ophaalvolgorde**.
1. Ga naar **Verkoop** > **Volgorde: een bestelling selecteren** en ga vervolgens naar **Informatie** en selecteert u **E-mail verzenden**.

<u>Verwachte resultaten</u>:

De bestelling-items worden zoals verwacht weergegeven in het e-mailbericht van de klant.

<u>Werkelijke resultaten</u>:

De orderitems ontbreken in de e-mail met de bestelbon van de klant. Hetzelfde geldt als u een nieuwe sjabloon maakt en een sjabloon Nieuwe volgorde of Nieuwe volgorde (Luma) selecteert.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
