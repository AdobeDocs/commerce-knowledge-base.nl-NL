---
title: 'MDVA-38827: Klanten ontvangen via e-mail een fout met betrekking tot het verzenden van orders'
description: "De MDVA-38827-patch verhelpt het probleem dat klanten een e-mail met een bestelling ontvangen met het volgende foutbericht: *Er is helaas een fout opgetreden bij het genereren van deze inhoud*. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0 is geïnstalleerd. De patch-id is MDVA-38827. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4."
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827: Klanten ontvangen per e-mail een fout bij het verzenden van orders

Met de MDVA-38827-patch is het probleem opgelost waarbij klanten een e-mail met een bestelling ontvangen die het volgende foutbericht bevat: *Er is helaas een fout opgetreden bij het genereren van deze inhoud*. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0 is geïnstalleerd. De patch-id is MDVA-38827. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer de optie Klanten per e-mail op de hoogte stellen voor verzending is geselecteerd, ontvangen klanten een e-mail met het volgende foutbericht: *Er is helaas een fout opgetreden bij het genereren van deze inhoud*.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Marketing** > **Communicatie** > **E-mailsjablonen** en selecteert u **Nieuwe sjabloon toevoegen**.
   * Selecteren **Verkoop Magento** > **Nieuwe verzending**.
   * Klikken op **Sjabloon laden**.
   * Voeg een sjabloonnaam toe (bijvoorbeeld Core Shipping Template) en klik op **Opslaan**.
1. Ga naar **Winkel** > Instellingen > **Configuratie** > **Verkoop** > **Verkoope-mail**:
   * Inschakelen **Opmerkingen bij verzending**.
   * Selecteren **Core Shipping-sjabloon** (Raadpleeg het gedeelte &#39;Een sjabloonnaam toevoegen&#39; van stap 1) onder E-mailsjabloon voor opmerkingen bij verzending en e-mailsjabloon voor opmerkingen bij verzending voor gasten.
1. Plaats een bestelling. Ga naar het deelvenster Beheer > **Verkoop** > **Volgorde**, klikt u op **Weergave** en verzend de bestelling.
1. De ordestatus verandert van In behandeling in Verwerking.
1. Klikken **Overbrengingen** op het linkerzijbalkmenu en klik vervolgens op **Weergave** om de bestelling te zien.
1. Een opmerking toevoegen in **Tekst opmerking** onder **Verzendgeschiedenis** en schakel het selectievakje in **De klant per e-mail op de hoogte stellen**.
1. Klikken **Opmerking verzenden**.

<u>Verwachte resultaten</u>:

Verkoop-e-mail met opmerkingen bij verzending wordt gegenereerd.

<u>Werkelijke resultaten</u>:

Het volgende foutbericht wordt ontvangen in de e-mail: *Er is helaas een fout opgetreden bij het genereren van deze inhoud.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
