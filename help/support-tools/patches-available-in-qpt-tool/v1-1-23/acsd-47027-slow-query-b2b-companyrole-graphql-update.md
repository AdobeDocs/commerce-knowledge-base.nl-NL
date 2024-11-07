---
title: 'ACSD-47027: langzame vraag B2B [!UICONTROL CompanyRole] [!DNL GraphQL]  update'
description: Pas ACSD-47027 flard toe om de kwestie van Adobe Commerce te bevestigen waar er een langzame vraag B2B [!UICONTROL CompanyRole] [!DNL GraphQL]  update is.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027: langzame query B2B [!UICONTROL CompanyRole] [!DNL GraphQL] bijwerken

De ACSD-47027-patch lost het probleem op waarbij de langzame query B2B [!UICONTROL CompanyRole] [!DNL GraphQL] -update niet werkt zoals u had verwacht. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 wordt geïnstalleerd. De patch-id is ACSD-47027. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De langzame B2B [!UICONTROL CompanyRole] [!DNL GraphQL] -update voor query werkt niet zoals verwacht.

<u> Eerste vereisten </u>:

Installeer de B2B-module.

<u> Stappen om </u> te reproduceren:

1. In Adobe Commerce Admin, ga **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** en reeks **[!UICONTROL Enable Company]** aan _ja_.
1. Ga naar de frontend en creeer een bedrijf.
1. Nadat u zich hebt aangemeld als bedrijfsgebruiker, gaat u naar **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** en voegt u een nieuwe rol toe.
1. Schakel [!UICONTROL dev] querylogboek in met `bin/magento dev:que:enab` .
1. Verzend nu de onderstaande aanvraag [!DNL GraphQL] (id is de [!UICONTROL base64] gecodeerde rol-id):

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. Controleer het querylogboek.
1. U ziet dat de bovenstaande query is uitgevoerd. Deze query wordt uitgevoerd in `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` .

<u> Verwachte resultaten </u>:

`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` moet worden geoptimaliseerd om te voorkomen dat alle gegevens in de **[!UICONTROL company_permissions]** DB-tabel worden geladen.

<u> Ware resultaten </u>:

Adobe Commerce voert een query uit zonder filter. Als er een groot aantal records is, kost het veel tijd voor Adobe Commerce om de gegevensverzameling voor te bereiden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe. 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
