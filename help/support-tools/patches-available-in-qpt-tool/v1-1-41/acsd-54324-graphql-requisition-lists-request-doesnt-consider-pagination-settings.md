---
title: 'ACSD-54324: Het verzoek GraphQL requisition_lists overweegt geen pagineringsinstellingen'
description: Pas het ACSD-54324 flard toe om de kwestie van Adobe Commerce te bevestigen waar het GraphQL ` requisition_lists' verzoek pagineringsmontages niet overweegt en alle resultaten terugkeert.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324: GraphQL `requisition_lists` verzoek houdt geen rekening met pagineringsinstellingen

De ACSD-54324-patch verhelpt het probleem waarbij de GraphQL `requisition_lists` Bij request wordt geen rekening gehouden met pagineringsinstellingen en worden alle resultaten geretourneerd. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.41 is geïnstalleerd. De patch-id is ACSD-54324. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De GraphQL `requisition_lists` Bij request wordt geen rekening gehouden met pagineringsinstellingen en worden alle resultaten geretourneerd.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij Beheer en navigeer naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Set *[!UICONTROL Enable Requisition List]* tot *Ja*.

1. Log in op de voorgrond en ga naar **[!UICONTROL My Requisition Lists]** in het bovenste menu of vanuit **[!UICONTROL My Account]** en maak meerdere aanvragen (bijvoorbeeld: 7).
1. Voer de onderstaande GraphQL uit nadat u een klanttoken hebt gegenereerd `requisition_lists` query voor de klant.

   * Zorg ervoor dat het paginaformaat kleiner is dan het totale aantal aanvraaglijsten dat u hebt gemaakt (bijvoorbeeld: 4)

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. Neem waar dat de waarde van `total_count` in het veld wordt 7 weergegeven, terwijl 4 wordt weergegeven.

   Het aantal objecten wordt ook weergegeven in 7 wanneer dit hetzelfde moet zijn als het *paginaformaat*.

<u>Verwachte resultaten</u>:

* Het nummer vermeld als *paginaformaat* is geretourneerd onder `total_count` en niet het totale aantal records.
* Het aantal items is gelijk aan het aantal *paginaformaat*.

<u>Werkelijke resultaten</u>:

Het totale aantal records is geretourneerd onder `total_count`, zelfs *paginaformaat* genoemd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
