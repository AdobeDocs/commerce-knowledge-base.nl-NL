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

De ACSD-50949-patch verhelpt het probleem dat het prijsfilter in de geavanceerde zoekopdracht geen goede resultaten oplevert wanneer het samen met het SKU-filter wordt gebruikt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-50949. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) . Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Probleem

Het prijsfilter in geavanceerd zoeken retourneert geen goede resultaten wanneer het samen met het SKU-filter wordt gebruikt.

<u> Stappen om </u> te reproduceren:

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

1. Open **[!UICONTROL Advanced Search]** op de Storefront en onderzoek door SKU: &quot;MJ&quot;.
1. Klik op de koppeling **[!UICONTROL Modify your search]** .
1. Voeg een prijswaaier aan de criteria van *1* aan *21* toe, en klik de **[!UICONTROL Search]** knoop.

<u> Verwachte resultaten </u>:

Alleen producten met prijzen binnen het gedefinieerde bereik worden geretourneerd.

<u> Ware resultaten </u>:

Producten met prijzen hoger dan *$21* worden geretourneerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] gids.
