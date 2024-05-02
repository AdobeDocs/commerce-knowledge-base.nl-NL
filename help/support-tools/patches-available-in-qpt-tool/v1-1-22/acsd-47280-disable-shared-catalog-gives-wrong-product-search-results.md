---
title: '''[!DNL ACSD-47280]: Gedeelde catalogus uitschakelen geeft onjuiste zoekresultaten voor het product"'
description: Pas de [!DNL ACSD-47280] repareren om de juiste zoekresultaten weer te geven wanneer de functie voor de gedeelde catalogus is uitgeschakeld.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: Als u de gedeelde catalogus uitschakelt, worden onjuiste zoekresultaten voor het product weergegeven

De [!DNL ACSD-47280] corrigeert de weergave van de juiste zoekresultaten wanneer de [!DNL shared catalog] is uitgeschakeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 is geïnstalleerd. De [!DNL patch ID] is [!DNL ACSD-47280]. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de [!DNL patch ID] als zoekwoord om de patch te zoeken.

## Probleem

Uitschakelen [!DNL shared catalog] geeft onjuiste resultaten bij het zoeken naar producten.

<u>Vereisten</u>:

* [!DNL B2B] geïnstalleerde modules

<u>Stappen om te reproduceren</u>:

1. Maak een tweede website.
1. Een product toewijzen aan de tweede website.
1. Producten controleren op de **tweede website** gebruiken [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. Inschakelen **[!UICONTROL Shared Catalog]** standaard [!DNL scope].
1. De [!DNL GraphQL] in de aanvraag worden geen producten voor de tweede website meer getoond , hetgeen het juiste resultaat is .
1. Ga naar de [!DNL scope] van tweede website en uitschakelen **[!UICONTROL Company]**.

<u>Verwachte resultaten</u>:

De [!DNL GraphQL] in het verzoek moeten nog producten voor de tweede website worden getoond .

<u>Werkelijke resultaten</u>:

De [!DNL GraphQL] in de aanvraag worden geen producten voor de tweede website weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
