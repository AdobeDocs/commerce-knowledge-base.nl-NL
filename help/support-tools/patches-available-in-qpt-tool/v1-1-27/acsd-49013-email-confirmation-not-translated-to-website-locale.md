---
title: 'ACSD-49013: e-mailbevestiging niet vertaald naar landinstelling van website'
description: Pas de ACSD-49013-patch toe om het Adobe Commerce-probleem op te lossen, waarbij e-mailbevestiging niet naar de landinstelling van de website wordt vertaald wanneer klanten met de bulk-API worden gemaakt.
exl-id: 68203bd4-021a-4736-a793-4b6663a9c66b
feature: Admin Workspace, Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49013: e-mailbevestiging niet vertaald naar landinstelling van website

De ACSD-49013-patch verhelpt het probleem waarbij e-mailbevestiging niet wordt vertaald naar de landinstelling van de website wanneer klanten met de bulk-API worden gemaakt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-49013. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mailbevestiging wordt niet vertaald naar de landinstelling van de website wanneer klanten met de bulk-API worden gemaakt.

<u>Stappen om te reproduceren</u>:

1. Een andere landinstelling installeren, zoals `de_DE`.
1. Configureren *RabbitMQ*.
1. Uitvoeren `bin/magento setup:upgrade` om de wachtrijen in RabbitMQ te installeren en het taalpakket in te stellen.
1. Een extra website maken in [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. De landinstelling van deze nieuwe website instellen op `de_DE` in [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**.
1. Voer een API-aanroep uit om een klantenaccount te maken met de bulk-API. Gebruik de bijbehorende `website_id`.

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. Uitvoeren `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`.
1. U kunt zien dat de klantenaccount op de opgegeven website correct is gemaakt.
1. Controleer het ontvangen e-mailbericht voor klantenregistratie.

<u>Verwachte resultaten</u>:

Aangezien de klant op een opgegeven website is gemaakt, wordt de registratie-e-mail verzonden met de landinstelling van die website.

<u>Werkelijke resultaten</u>:

De klant is op de juiste wijze gemaakt op de opgegeven website, maar de registratie-e-mail wordt verzonden met de standaardlandinstelling wanneer de bulk-API wordt gebruikt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
