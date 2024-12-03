---
title: 'ACSD-54324: Het verzoek GraphQL requisition_lists overweegt geen pagineringsmontages'
description: Pas het ACSD-54324 flard toe om de kwestie van Adobe Commerce te bevestigen waar het GraphQL ` requisition_lists' verzoek pagineringsmontages niet overweegt en alle resultaten terugkeert.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324: GraphQL `requisition_lists` -aanvraag houdt geen rekening met pagineringsinstellingen

De ACSD-54324-patch verhelpt het probleem dat in de GraphQL `requisition_lists` -aanvraag geen aandacht wordt besteed aan pagineringsinstellingen en retourneert alle resultaten. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.41 wordt geïnstalleerd. De patch-id is ACSD-54324. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De GraphQL `requisition_lists` -aanvraag houdt geen rekening met pagineringsinstellingen en retourneert alle resultaten.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij Beheer en navigeer naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** .

   * Plaats *[!UICONTROL Enable Requisition List]* aan *ja*.

1. Meld u aan bij de voorzijde en ga naar **[!UICONTROL My Requisition Lists]** in het bovenste menu of vanuit **[!UICONTROL My Account]** en maak meerdere aanvragen (bijvoorbeeld 7).
1. Nadat u een klanttoken hebt gegenereerd, voert u de onderstaande GraphQL `requisition_lists` -query voor de klant uit.

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

1. De waarde van het veld `total_count` geeft 7 weer, terwijl de waarde 4 moet worden weergegeven.

   Het aantal punten toont ook 7 wanneer het het zelfde als de *paginagrootte* zou moeten zijn.

<u> Verwachte resultaten </u>:

* Het aantal dat als *wordt vermeld paginagrootte* is teruggekeerd onder `total_count` en niet het totale aantal verslagen.
* Het aantal punten is het zelfde als de *paginagrootte*.

<u> Ware resultaten </u>:

Het totale aantal verslagen is teruggekeerd onder `total_count`, zelfs als *paginagrootte* wordt vermeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
