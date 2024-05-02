---
title: "ACSD-47292: gebundelde producten uit de voorraad zijn niet beschikbaar in GraphQL-respons"
description: Pas de ACSD-47292-patch toe om het Adobe Commerce-probleem op te lossen waarbij de gebundelde producten uit de voorraad niet beschikbaar zijn in de GraphQL-respons, zelfs als de "producten uit de voorraad tonen" op Ja is ingesteld.
exl-id: 377dc62f-d1cd-4292-b25d-53c498b772a9
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# ACSD-47292: gebundelde producten uit de voorraad zijn niet beschikbaar in GraphQL-respons

De ACSD-47292-patch verhelpt het probleem dat gebundelde producten uit de voorraad niet beschikbaar zijn in de GraphQL-respons, zelfs als de [!UICONTROL Display Out-of-Stock Products] is ingesteld op *[!UICONTROL Yes]*. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 is geïnstalleerd. De patch-id is ACSD-47292. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebundelde producten uit de voorraad zijn niet beschikbaar in het GraphQL-antwoord, zelfs niet als de [!UICONTROL Display Out-of-Stock Products] is ingesteld op *[!UICONTROL Yes]*.

<u>Stappen om te reproduceren</u>:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** en stelt de [!UICONTROL Display Out-of-Stock Products] tot *[!UICONTROL Yes]*.
1. Maak twee eenvoudige producten, s1 en s2.
1. Maak s1 uit-van-voorraad en niet zichtbaar individueel en s2 in-voorraad en niet zichtbaar individueel, en wijs hen aan een categorie toe.
1. Maak een gebundeld product met ten minste één optieproduct en wijs s1 en s2 aan deze optie toe (invoertype &quot;RadioButton&quot;).
1. Sla het gebundelde product op en wijs het toe aan een categorie.
1. Ga naar de winkel en open dit gebundelde product. U zult zien dat de optie s1 buiten de voorraad grijs maar zichtbaar is.
1. Een GraphQL-aanvraag verzenden:

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>Verwachte resultaten</u>:

s1-bundeloptie wordt vermeld in de GraphQL-reactie omdat [!UICONTROL Display Out-of-Stock Products] is ingesteld op *[!UICONTROL Yes]* en is zichtbaar op de winkel.

<u>Werkelijke resultaten</u>:

s1-bundeloptie wordt niet vermeld in GraphQL-reactie.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
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
