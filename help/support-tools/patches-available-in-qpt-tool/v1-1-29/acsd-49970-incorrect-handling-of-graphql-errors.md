---
title: "ACSD-49970: onjuiste afhandeling van GraphQL-fouten"
description: Pas de ACSD-49970-patch toe om het Adobe Commerce-probleem op te lossen wanneer GraphQL-fouten onjuist worden afgehandeld [!UICONTROL New Relic Reporting] is ingeschakeld.
exl-id: 70acade5-02a5-4769-86e2-5c566b2af709
feature: GraphQL, Observability
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49970: onjuiste afhandeling van GraphQL-fouten

De ACSD-49970-patch verhelpt het probleem bij een onjuiste verwerking van GraphQL-fouten *[!UICONTROL New Relic Reporting]* is ingeschakeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-49970. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`GraphQLOperationNames` toets wordt niet correct verwerkt of de `logDataHelper` bevat deze sleutel of niet.

<u>Stappen om te reproduceren</u>:

1. Uitvoeren `bin/magento deploy:mode:set developer`.
1. Meld u aan bij de beheerder.
1. Inschakelen **[!UICONTROL New Relic Integration]** van **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(Opmerking: zelfs als er een fout wordt weergegeven met de melding dat de [!DNL New Relic] -extensie niet beschikbaar is, wordt de configuratie opgeslagen).
1. Dit uitvoeren *GraphQL* mutatie naar `http://yourMagentoDomain/graphql` van de *[!DNL Altair]* client of een andere client of via cURL.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Opmerking: stel de **[!UICONTROL Header]** tot [!UICONTROL Content-Currency:CA] voordat u het programma uitvoert).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Verwachte resultaten</u>:

Er is *500 uitzondering* in logboeken, `GraphQLOperationNames` sleutel wordt correct verwerkt.

<u>Werkelijke resultaten</u>:

Er is een *500 uitzondering* in logboeken, `GraphQLOperationNames` sleutel wordt niet correct verwerkt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
