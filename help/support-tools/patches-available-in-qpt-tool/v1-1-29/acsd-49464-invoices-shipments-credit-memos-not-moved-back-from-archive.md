---
title: "ACSD-49464: facturen, overbrengingen en creditnota's niet terug van archief"
description: Pas de ACSD-49464-patch toe om het Adobe Commerce-probleem op te lossen, waarbij facturen, verzendingen en creditnota's niet uit het archief worden verplaatst wanneer de orderId anders is.
exl-id: 845f9878-5f7e-4e58-8f8a-b02af17b3f11
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-49464: facturen, overbrengingen en creditnota&#39;s niet van archief worden verplaatst

De ACSD-49464-patch verhelpt het probleem waarbij facturen, verzendingen en creditnota&#39;s niet uit archief worden verplaatst wanneer orderId anders is. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-49464. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Facturen, verzendingen en creditnota&#39;s worden niet uit het archief verplaatst wanneer orderId anders is.

<u>Stappen om te reproduceren</u>:

1. Opdrachten, facturen, verzendingen en archivering van creditnota&#39;s inschakelen.
1. Maak en voltooi een bestelling, inclusief verzending, factuur en creditnota.
1. Zorg ervoor dat de verzend-, factuur- en creditnota-id&#39;s niet hetzelfde zijn als het ordernummer.
1. De volgorde verplaatsen naar archief.
1. Herstel de gearchiveerde bestelling naar orderbeheer.
1. Controleer de factuurgegevens, de verzendgegevens en de gegevens over de creditcard in de respectieve landen [!UICONTROL Invoice], [!UICONTROL Shipping], en [!UICONTROL Credit Memo] rasterpagina&#39;s.

<u>Verwachte resultaten</u>:

De oorspronkelijke verwante records worden hersteld wanneer de volgorde wordt verplaatst van de archieflijst naar het orderbeheer.

<u>Werkelijke resultaten</u>:

* Geen administratie voor verzending, factuur en creditnota&#39;s als alle id&#39;s verschillend zijn.
* Als de orde en verwante verslagen zelfde identiteitskaart hebben, dan zijn de verslagen teruggekeerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
