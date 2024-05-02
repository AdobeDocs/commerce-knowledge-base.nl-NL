---
title: 'ACSD-51120: GraphQL GET request cache not clear for CMS pages that contain CMS block'
description: Pas de ACSD-51120-patch toe om het Adobe Commerce-probleem op te lossen waarbij de GraphQL-GET-aanvraagcache niet wordt gewist voor CMS-pagina's die CMS-blokken bevatten.
exl-id: 22abba89-b697-45d7-972e-bf3233e5e9ec
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-51120: GraphQL GET request cache is niet gewist voor CMS-pagina&#39;s die CMS-blokken bevatten

De ACSD-51120-patch verhelpt het probleem waarbij de GraphQL GET request-cache niet wordt gewist voor CMS-pagina&#39;s die CMS-blokken bevatten die via een testupdate worden bijgewerkt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-51120. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De GraphQL GET request cache wordt niet gewist voor CMS-pagina&#39;s die CMS-blokken bevatten die via een testupdate worden bijgewerkt.

<u>Stappen om te reproduceren</u>:

1. Maak een CMS-blok.
1. Neem het CMS-blok op in een CMS-pagina met de opdracht [!DNL Page Builder].
1. Zoek de CMS-pagina met de opgegeven GraphQL-query op een GET-aanvraag:

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. Controleer of de GraphQL-reactie in de cache is geplaatst [!DNL Varnish].
1. Maak een geplande update voor het blok.
1. Wacht tot de geplande update is toegepast en voer de uitsnijdtaak uit om de geplande update toe te passen.
1. Haal de CMS-pagina opnieuw op met de opgegeven GraphQL-query op een GET-verzoek.

<u>Verwachte resultaten</u>:

In het antwoord wordt de bijgewerkte inhoud weergegeven.

<u>Werkelijke resultaten</u>:

De reactie toont nog steeds de oude inhoud.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
