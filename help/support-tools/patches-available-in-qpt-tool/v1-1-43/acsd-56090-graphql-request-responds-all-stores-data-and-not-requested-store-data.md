---
title: 'ACSD-56090: GraphQL-respons is niet opslagspecifiek'
description: Pas de ACSD-56090-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het GraphQL-antwoord alle opslaggegevens bevat in plaats van de opslagspecifieke gegevens.
feature: GraphQL
role: Admin, Developer
exl-id: 129491e0-1a77-4ccc-8aba-cd0afdb26176
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56090: GraphQL-respons is niet specifiek opgeslagen

De ACSD-56090-patch verhelpt het probleem waarbij de GraphQL reageert, alle opslaggegevens bevat in plaats van de opslagspecifieke gegevens. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 is geïnstalleerd. De patch-id is ACSD-56090. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL-reactie bevat alle opslaggegevens in plaats van de opslagspecifieke gegevens.

<u>Stappen om te reproduceren</u>:

1. Aanmelden bij **[!UICONTROL Admin panel]** > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** en maakt u twee hoofdcategorieën.
1. Elke basiscategorie moet één subcategorie hebben.
1. Navigeren naar **[!UICONTROL Stores]** > **[!UICONTROL All stores]** > Twee opslagruimten hebben verschillende hoofdcategorieën voor elk ervan. (Elke winkel moet minstens één winkelweergave hebben)
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Een product maken met

* Alle toegewezen hoofdcategorieën en subcategorieën
* Alle toegewezen websites.

1. Voer de query GraphqQL uit (voeg header toe — store = &#39;storename&#39;):

```
   query {
     products(filter: { url_key: { eq: "abc" } }) {
       items {
         categories {
           name
           id
           url_path
           breadcrumbs {
             category_id
             category_name
             category_level
           }
         }
       }
     }
   }
```

1. Controleer de reactie na het uitvoeren van de vraag GraphqQL.

<u>Verwachte resultaten</u>:

De opslagspecifieke gegevens worden geretourneerd

<u>Werkelijke resultaten</u>:

De geretourneerde gegevens zijn niet specifiek opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
