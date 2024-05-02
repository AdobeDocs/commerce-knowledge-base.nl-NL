---
title: 'ACSD-51041: Prijsindex duurt erg lang om te voltooien'
description: Pas de ACSD-51041-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de prijsindex lang duurt om te voltooien met een zeer grote productset.
exl-id: 442f5eae-ca00-4329-be24-68970624928f
feature: Configuration
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-51041: Het duurt erg lang om de prijsindex te voltooien

De ACSD-51041-patch verhelpt het probleem waarbij de prijsindex lang duurt om te voltooien met een zeer grote productset. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 is geïnstalleerd. De patch-id is ACSD-51041. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Met een zeer grote productset duurt het erg lang om de prijsindex te voltooien.

<u>Stappen om te reproduceren</u>:

1. De optie *[!UICONTROL Inventory]* -module.
1. Meerdere aandelenbronnen hebben (met een bron zonder wanbetaling die het grootste deel van de voorraad levert).
1. ~200k producten genereren.
1. Voer een inventarisindex uit.

<u>Verwachte resultaten</u>:

`deleteIndexData` verwerkt alleen de unieke id&#39;s om de prestaties te optimaliseren.

<u>Werkelijke resultaten</u>:

`deleteIndexData` verwerkt alle id&#39;s, die lang duren.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
