---
title: '"ACSD-53176: Productregel met ''is een van''-voorwaarde komt niet overeen'''
description: Pas de ACSD-53176-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de gerelateerde productregel 'één van' niet correct werkt voor 'Producten afstemmen'.
feature: Marketing Tools
role: Admin
exl-id: 91f05f5b-6a5e-4b93-9dfb-88cbeccb6c9e
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-53176: Productregel met `is one of` voorwaarde komt niet overeen

De ACSD-53176-patch verhelpt het probleem waarbij de gerelateerde productregel `is one of` voorwaarde werkt niet correct voor **Producten afstemmen**. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.36 is geïnstalleerd. De patch-id is ACSD-53176. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

The related product rule `is one of` voorwaarde werkt niet correct voor **Producten afstemmen**.

<u>Stappen om te reproduceren</u>:

1. Maak 3-4 producten.
1. Maak een nieuwe regel voor verwante producten.

   Stel de regel in op twee of meer producten:
   * `SKU is one of "S1,S2".`

   Stel de regel in om twee of meer items weer te geven:
   * `Product SKU is one of constant value "S2,S3".`

1. Open het S1 product op de Storefront.

<u>Verwachte resultaten</u>:

De verwante producten &quot;S2&quot; en &quot;S3&quot; worden weergegeven op zowel productpagina&#39;s &quot;S1&quot; als &quot;S2&quot;.

<u>Werkelijke resultaten</u>:

Verwante producten worden niet weergegeven op de productpagina&#39;s.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
