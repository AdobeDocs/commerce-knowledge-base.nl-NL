---
title: 'ACSD-47027: langzame query B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update'
description: Pas de ACSD-47027-patch toe om het Adobe Commerce-probleem op te lossen in geval van een langzame query B2B [!UICONTROL CompanyRole] [!DNL GraphQL] bijwerken.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027: langzame query B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update

De ACSD-47027-patch lost het probleem op waarbij de langzame query B2B [!UICONTROL CompanyRole] [!DNL GraphQL] de update werkt niet zoals verwacht. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 is geïnstalleerd. De patch-id is ACSD-47027. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**
* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De langzame vraag B2B [!UICONTROL CompanyRole] [!DNL GraphQL] de update werkt niet zoals verwacht.

<u>Vereisten</u>:

Installeer de B2B-module.

<u>Stappen om te reproduceren</u>:

1. Ga in Adobe Commerce Admin naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** en instellen **[!UICONTROL Enable Company]** tot _Ja_.
1. Ga naar de frontend en creeer een bedrijf.
1. Nadat u zich als bedrijfgebruiker hebt aangemeld, gaat u naar **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** en voeg een nieuwe rol toe.
1. Inschakelen [!UICONTROL dev] querylogboek gebruiken `bin/magento dev:que:enab`.
1. Stuur nu de onderstaande [!DNL GraphQL] request (id is de [!UICONTROL base64] gecodeerde rol-id):

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
1. U ziet dat de bovenstaande query is uitgevoerd. Deze query wordt uitgevoerd in `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Verwachte resultaten</u>:

De `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` moet worden geoptimaliseerd om te voorkomen dat alle in het **[!UICONTROL company_permissions]** DB-tabel.

<u>Werkelijke resultaten</u>:

Adobe Commerce voert een query uit zonder filter. Als er een groot aantal records is, kost het veel tijd voor Adobe Commerce om de gegevensverzameling voor te bereiden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie. 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
