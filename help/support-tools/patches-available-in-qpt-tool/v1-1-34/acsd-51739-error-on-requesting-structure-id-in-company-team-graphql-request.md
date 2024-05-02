---
title: "ACSD-51739: Error on request ` structure_id` in ` CompanyTeam` GraphQL request"
description: Pas ACSD-51739 flard toe om de kwestie van Adobe Commerce te bevestigen waar een fout is teruggekeerd wanneer ` structure_id ` in een ` CompanyTeam ` GraphQL verzoek wordt gevraagd.
exl-id: 31c085e0-c8be-4709-9620-80ff360dca9a
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739: Fout bij aanvragen `structure_id` in `CompanyTeam` GraphQL-verzoek

De ACSD-51739-patch verhelpt het probleem waarbij een fout wordt geretourneerd wanneer de `structure_id` wordt gevraagd in een `CompanyTeam` GraphQL request. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 is geïnstalleerd. De patch-id is ACSD-51739. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een fout geretourneerd wanneer de `structure_id` wordt gevraagd in een `CompanyTeam` GraphQL request.

<u>Stappen om te reproduceren</u>

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**, en instellen *[!UICONTROL Enable Company]* tot *Ja*.
1. Creeer een bedrijf samen met een bedrijf admin gebruiker.
1. Een nieuwe klant maken (*klant1*) en het bedrijf (hierboven gemaakt) aan deze klant toewijzen.
1. Voor frontend, login als bedrijf admin gebruiker.
1. Creeer een bedrijfsteam, en wijs toe *klant1* naar het team slepen met slepen en neerzetten.
1. Voer de volgende query voor GraphQl van het bedrijf uit, waaronder `CompanyTeam` with `structure_id`:

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. Controleer het GraphQL-antwoord.

<u>Verwachte resultaten</u>:

Er worden geen fouten geretourneerd en alle aangevraagde gegevens bevinden zich in de GraphQL-reactie.

<u>Werkelijke resultaten</u>:

* De reactie bevat een *Interne serverfout*.
* `var/log/exception.log` bevat:

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
