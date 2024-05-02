---
title: "ACSD-47079: voorraadstatus van samengestelde producten niet bijgewerkt wanneer de voorraadstatus van subproducten verandert"
description: Pas de ACSD-47079-patch toe om het Adobe Commerce-probleem op te lossen waarbij de status van de voorraad van samengestelde producten (bundel, gegroepeerd en configureerbaar) niet wordt bijgewerkt wanneer de status van de voorraad van subproducten verandert via REST API POST /rest/V1/voorraad/bron-items.
exl-id: 603e4548-fb04-43b4-a033-4f2c7f665fae
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-47079: voorraadstatus van samengestelde producten niet bijgewerkt wanneer de voorraadstatus van subproducten verandert

De ACSD-47079-patch verhelpt het probleem dat de voorraadstatus van samengestelde producten (bundel, gegroepeerd en configureerbaar) niet wordt bijgewerkt wanneer de status van de voorraad van het subproduct via REST API-POST wordt gewijzigd `/rest/V1/inventory/source-items`. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-47079. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De voorraadstatus van samengestelde producten (bundel, gegroepeerd en configureerbaar) wordt niet bijgewerkt wanneer de voorraadstatus van het subproduct via REST API-POST wordt gewijzigd `/rest/V1/inventory/source-items`.

<u>Stappen om te reproduceren</u>:

1. Creeer een configureerbaar, gebundeld, en gegroepeerd product met één eenvoudig kindproduct voor elk.
1. Elke eenvoudige status van een onderliggende product instellen op **[!UICONTROL Out of Stock]** met de `source-items` API-aanroep.
1. Controleer nu de voorraadstatus van het bovenliggende product.

<u>Verwachte resultaten</u>:

De status van het bovenliggende product is [!UICONTROL Out of Stock].

<u>Werkelijke resultaten</u>:

De status van het bovenliggende product is [!UICONTROL In Stock].

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
