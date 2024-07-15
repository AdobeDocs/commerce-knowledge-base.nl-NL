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

De ACSD-56090-patch verhelpt het probleem waarbij de GraphQL reageert, alle opslaggegevens bevat in plaats van de opslagspecifieke gegevens. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 wordt geïnstalleerd. De patch-id is ACSD-56090. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL-reactie bevat alle opslaggegevens in plaats van de opslagspecifieke gegevens.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij **[!UICONTROL Admin panel]** > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** en maak twee hoofdcategorieën.
1. Elke basiscategorie moet één subcategorie hebben.
1. Navigeer naar **[!UICONTROL Stores]** > **[!UICONTROL All stores]** > Twee winkels hebben verschillende hoofdcategorieën. (Elke winkel moet minstens één winkelweergave hebben)
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

<u> Verwachte resultaten </u>:

De opslagspecifieke gegevens worden geretourneerd

<u> Ware resultaten </u>:

De geretourneerde gegevens zijn niet specifiek opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
