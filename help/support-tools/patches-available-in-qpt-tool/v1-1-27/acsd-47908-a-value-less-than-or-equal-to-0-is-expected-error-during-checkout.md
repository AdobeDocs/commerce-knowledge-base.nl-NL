---
title: 'ACSD-47908: *Er wordt een fout van het type *Een waarde kleiner dan of gelijk aan 0 verwacht* tijdens het uitchecken'
description: Pas de ACSD-47908-patch toe om de Adobe Commerce-fout *Er wordt een waarde van minder dan of gelijk aan 0 verwacht* bij het selecteren van de bron en het aantal bij de verzendstap tijdens het afrekenen.
exl-id: fec90e4b-9cb8-4cd9-9e85-ccada840c896
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908: *de waarde van A minder dan of gelijk aan 0 wordt verwacht* fout tijdens controle

Het ACSD-47908 flard bevestigt de fout *waarde A minder dan of gelijk aan 0 wordt verwacht* wanneer het selecteren van de bron en de hoeveelheid in de verschepende stap tijdens controle. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-47908. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De volgende fout wordt geworpen wanneer het selecteren van de bron en de hoeveelheid in de verschepende stap tijdens controle: *de waarde van A minder dan of gelijk aan 0 wordt verwacht*.

<u> Eerste vereisten </u>:

Installeer de Adobe Commerce Inventory management-modules (MSI).

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** en configureer meerdere bronnen.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** en maak een nieuwe voorraad.
   * Wijs nu de bronnen toe aan de nieuwe voorraad.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en bewerk ten minste één product.
   * Controleer of de producten aan de nieuwe bronnen zijn toegewezen en geef de beschikbare hoeveelheid op.
1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** en maak een nieuwe volgorde.
1. Voeg die producten aan de orde toe en plaats het.
1. Klik op **[!UICONTROL Ship]**.
1. Selecteer de bron waaruit u wilt verzenden.
1. Geef de hoeveelheid van elk object op die moet worden verzonden.
1. Laad de pagina opnieuw.
1. Klik op **[!UICONTROL Proceed to Shipment]** .

<u> Verwachte resultaten </u>:

De nieuwe verzendpagina wordt zonder fouten geopend.

<u> Ware resultaten </u>:

* De ingevoerde hoeveelheid kan niet worden gevalideerd.
* De volgende fout wordt geworpen: *gelieve te gaan een waarde minder dan of gelijk aan 0* in.

  De fout is echter inconsistent en wordt mogelijk niet altijd weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
