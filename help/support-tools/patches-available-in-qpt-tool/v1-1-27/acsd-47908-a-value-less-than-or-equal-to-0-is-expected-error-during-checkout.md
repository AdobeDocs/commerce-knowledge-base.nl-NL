---
title: 'ACSD-47908: *Er wordt een fout verwacht van een waarde kleiner dan of gelijk aan 0* tijdens het uitchecken.'
description: Pas de ACSD-47908-patch toe om de Adobe Commerce-fout *Er wordt een waarde van minder dan of gelijk aan 0 verwacht* bij het selecteren van de bron en het aantal bij de verzendstap tijdens het afrekenen.
exl-id: fec90e4b-9cb8-4cd9-9e85-ccada840c896
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908: *Een waarde kleiner dan of gelijk aan 0 wordt verwacht* fout tijdens uitchecken

De fout is opgelost met de ACSD-47908-patch *Een waarde kleiner dan of gelijk aan 0 wordt verwacht* bij het selecteren van de bron en hoeveelheid in de verzendstap tijdens het afrekenen. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-47908. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De volgende fout treedt op wanneer u de bron en het aantal in de verzendstap selecteert tijdens het uitchecken: *Een waarde kleiner dan of gelijk aan 0 wordt verwacht*.

<u>Vereisten</u>:

Installeer de Adobe Commerce Inventory management-modules (MSI).

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** en configureer meerdere bronnen.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** en maak een nieuwe voorraad.
   * Wijs nu de bronnen toe aan de nieuwe voorraad.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en bewerk ten minste één product.
   * Controleer of de producten aan de nieuwe bronnen zijn toegewezen en geef de beschikbare hoeveelheid op.
1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** en maakt u een nieuwe volgorde.
1. Voeg die producten aan de orde toe en plaats het.
1. Klik op **[!UICONTROL Ship]**.
1. Selecteer de bron waaruit u wilt verzenden.
1. Geef de hoeveelheid van elk object op die moet worden verzonden.
1. Laad de pagina opnieuw.
1. Klikken op **[!UICONTROL Proceed to Shipment]**.

<u>Verwachte resultaten</u>:

De nieuwe verzendpagina wordt zonder fouten geopend.

<u>Werkelijke resultaten</u>:

* De ingevoerde hoeveelheid kan niet worden gevalideerd.
* De volgende fout wordt gegenereerd: *Voer een waarde kleiner dan of gelijk aan 0 in*.

  De fout is echter inconsistent en wordt mogelijk niet altijd weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
