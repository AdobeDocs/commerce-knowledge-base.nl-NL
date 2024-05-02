---
title: 'ACSD-50949: Het prijsfilter in geavanceerd zoeken retourneert geen goede resultaten wanneer het samen met het SKU-filter wordt gebruikt'
description: Pas de ACSD-50949-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het prijsfilter in de geavanceerde zoekopdracht geen goede resultaten oplevert wanneer het samen met het SKU-filter wordt gebruikt.
feature: Orders, Search
role: Admin
exl-id: 3e1f88dc-07f6-4e10-b4b7-163648076cbc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 1%

---

# ACSD-50949: Prijsfilter in geavanceerd zoeken retourneert geen goede resultaten bij gebruik met SKU-filter

De ACSD-50949-patch verhelpt het probleem dat het prijsfilter in de geavanceerde zoekopdracht geen goede resultaten oplevert wanneer het samen met het SKU-filter wordt gebruikt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-50949. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Probleem

Het prijsfilter in geavanceerd zoeken retourneert geen goede resultaten wanneer het samen met het SKU-filter wordt gebruikt.

<u>Stappen om te reproduceren</u>:

1. Maak bijvoorbeeld meerdere producten:

   | SKU | Naam | Prijs | Aantal |
   |-----|-----------|-------|----------|
   | MJ1 | Product 1 | $ 10 | 10 |
   | MJ2 | Product 2 | $ 15 | 10 |
   | MJ3 | Product 3 | $ 21 | 10 |
   | MJ4 | Product 4 | $ 32 | 10 |
   | MJ5 | Product 5 | $ 33 | 10 |
   | MJ6 | Product 6 | $ 34 | 10 |
   | MJ7 | Product 7 | $ 44 | 10 |

1. Open de **[!UICONTROL Advanced Search]** op de Storefront en zoek door SKU: &quot;MJ&quot;.
1. Klik op de knop **[!UICONTROL Modify your search]** koppeling.
1. Voeg een prijsbereik toe aan de criteria van *1* tot *21* en klik op de knop **[!UICONTROL Search]** knop.

<u>Verwachte resultaten</u>:

Alleen producten met prijzen binnen het gedefinieerde bereik worden geretourneerd.

<u>Werkelijke resultaten</u>:

Producten met hogere prijzen dan *$ 21* worden geretourneerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
