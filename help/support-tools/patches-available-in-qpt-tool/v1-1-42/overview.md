---
title: '"Overzicht: [!DNL Quality Patches Tool] (QPT) v1.1.42'''
description: In deze subsectie vindt u een gedetailleerde beschrijving van de problemen die worden opgelost door de patches die beschikbaar zijn in [!DNL Quality Patches Tool] (QPT) v1.1.42.
feature: Tools and External Services
role: Admin, Developer
exl-id: 49f7ebd6-7a5f-49da-8fac-c3c2b73b52c1
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Overzicht: [!DNL Quality Patches Tool] (QPT) v1.1.42

In deze subsectie vindt u een gedetailleerde beschrijving van de problemen die worden opgelost door de patches die beschikbaar zijn in [!DNL Quality Patches Tool] (QPT) v1.1.42.

QPT v1.1.42 omvat de volgende flarden:

1. **ACSD-53658**: Hiermee wordt het probleem opgelost waarbij *[!UICONTROL Recently Viewed]* De productgegevens worden niet correct bijgewerkt in de winkelweergave.
1. **ACSD-54626**: Hiermee kunt u het probleem verhelpen waarbij u geen nieuwe regel voor inkooporders kunt maken (`createPurchaseOrderApprovalRule`) met de `NUMBER_OF_SKUS` via GraphQL.
1. **ACSD-53845**: Hiermee wordt het probleem met de MySQL-verbindingstijd verholpen wanneer `consumer max_messages` = 0.
1. **ACSD-54890**: Hiermee wordt het probleem opgelost waarbij `aggregate_sales_report_bestsellers_data` veroorzaakt MySQL-fouten vanwege `/tmp` schijf heeft onvoldoende ruimte.
1. **ACSD-55112**: Hiermee wordt het probleem opgelost waarbij de *[!UICONTROL Submit review]* er kan meerdere keren op de knop worden geklikt zonder [!DNL Google reCAPTCHA v3] validatie.
1. **ACSD-54264**: Hiermee wordt het probleem verholpen waarbij het foutbericht *U kunt het gevraagde kenmerk niet bijwerken. Rij-id: store_id* verschijnt wanneer een klant probeert uit te checken met een verhandelbaar aanhalingsteken in een andere winkelweergave.
1. **ACSD-54418**: Hiermee wordt de kwestie opgelost waarbij een vaste korting onjuist wordt toegepast op elk onderliggend product van de dynamisch geprijsde bundel.
1. **ACSD-55238**: Hiermee kunt u het probleem verhelpen door de lege metagegevensbeschrijving van het product op te slaan.
1. **ACSD-54966**: Hiermee wordt de emissie gecorrigeerd waarbij een couponcode met een beperkt gebruik per klant niet opnieuw kan worden gebruikt als de vorige bestelling is mislukt.
1. **ACSD-54060**: Hiermee wordt het probleem verholpen waarbij een beperkte beheerder een product niet kan opslaan als het een onderliggend product is van een ander product dat aan een ander bereik is toegewezen.
1. **ACSD-48910**: Hiermee wordt de kwestie opgelost waarbij een gebundeld product dat aan meerdere bronnen is toegewezen, uit voorraad raakt nadat een bestelling is gefactureerd en verzonden, zelfs als het een hoeveelheid heeft die niet gelijk is aan nul.
1. **ACSD-55381**: Oplossing voor een interne serverfout bij het opvragen `configurable_product_option_uid` en `configurable_product_option_value_uid` velden van een B2B *[!UICONTROL Requisition list]* via GraphQL.
1. **ACSD-55628**: Hiermee wordt het uploaden van een bestand in het bedrijfsregistratieformulier en het vervangen van een bestand voor een klantkenmerk in de winkel opgelost.

Gebruik het menu links om naar een specifieke patchpagina te navigeren.
