---
title: 'ACSD-49970: onjuiste afhandeling van GraphQL-fouten'
description: Pas de ACSD-49970-patch toe om het Adobe Commerce-probleem op te lossen wanneer GraphQL-fouten onjuist worden afgehandeld wanneer [!UICONTROL New Relic Reporting] wordt ingeschakeld.
exl-id: 70acade5-02a5-4769-86e2-5c566b2af709
feature: GraphQL, Observability
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49970: onjuiste afhandeling van GraphQL-fouten

De ACSD-49970-patch verhelpt het probleem waarbij GraphQL-fouten onjuist worden afgehandeld wanneer *[!UICONTROL New Relic Reporting]* wordt ingeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-49970. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`GraphQLOperationNames` -toets wordt niet correct afgehandeld, ongeacht of `logDataHelper` deze toets bevat of niet.

<u> Stappen om </u> te reproduceren:

1. Voer `bin/magento deploy:mode:set developer` uit.
1. Meld u aan bij de beheerder.
1. **[!UICONTROL New Relic Integration]** inschakelen vanuit **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(Opmerking: zelfs als er een fout wordt weergegeven met de mededeling dat de extensie [!DNL New Relic] niet beschikbaar is, wordt de configuratie opgeslagen.)
1. Stel dit *GraphQL* mutatie aan `http://yourMagentoDomain/graphql` van de *[!DNL Altair]* cliënt of een andere cliënt of via cURL in werking.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Opmerking: stel de **[!UICONTROL Header]** in op [!UICONTROL Content-Currency:CA] voordat u deze uitvoert).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u> Verwachte resultaten </u>:

Er is geen *500 uitzondering* in logboeken, `GraphQLOperationNames` de sleutel wordt correct behandeld.

<u> Ware resultaten </u>:

Er is a *500 uitzondering* in logboeken, `GraphQLOperationNames` de sleutel wordt niet correct behandeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
