---
title: '[!DNL ACSD-47280]: wanneer u de gedeelde catalogus uitschakelt, krijgt u onjuiste zoekresultaten voor het product'
description: Pas het  [!DNL ACSD-47280]  flard toe om het tonen van de correcte onderzoeksresultaten te bevestigen wanneer de gedeelde cataloguseigenschap gehandicapt is.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: Als u de gedeelde catalogus uitschakelt, worden onjuiste zoekresultaten voor het product weergegeven

De patch [!DNL ACSD-47280] corrigeert de weergave van de juiste zoekresultaten wanneer de functie [!DNL shared catalog] is uitgeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 wordt geïnstalleerd. De waarde [!DNL patch ID] is [!DNL ACSD-47280] . Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik [!DNL patch ID] als zoektrefwoord om de patch te zoeken.

## Probleem

Als u [!DNL shared catalog] uitschakelt, levert dit onjuiste zoekresultaten op.

<u> Eerste vereisten </u>:

* [!DNL B2B] geïnstalleerde modules

<u> Stappen om </u> te reproduceren:

1. Maak een tweede website.
1. Een product toewijzen aan de tweede website.
1. De producten van de controle op de **tweede website** gebruikend [!DNL GraphQL]:

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

1. **[!UICONTROL Shared Catalog]** inschakelen bij standaard [!DNL scope] .
1. In de aanvraag [!DNL GraphQL] worden geen producten voor de tweede website meer weergegeven. Dit is het juiste resultaat.
1. Ga naar de [!DNL scope] tweede website en schakel **[!UICONTROL Company]** uit.

<u> Verwachte resultaten </u>:

In de aanvraag [!DNL GraphQL] moeten nog steeds producten voor de tweede website worden weergegeven.

<u> Ware resultaten </u>:

In de aanvraag [!DNL GraphQL] worden geen producten voor de tweede website weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
