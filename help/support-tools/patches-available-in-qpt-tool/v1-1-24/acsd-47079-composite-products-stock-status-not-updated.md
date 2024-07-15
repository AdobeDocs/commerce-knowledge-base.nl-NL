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

De ACSD-47079-patch verhelpt het probleem dat de voorraadstatus van samengestelde producten (bundel, gegroepeerd en configureerbaar) niet wordt bijgewerkt wanneer de status van de voorraad van het subproduct via REST API-POST `/rest/V1/inventory/source-items` wordt gewijzigd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-47079. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De voorraadstatus van samengestelde producten (bundel, gegroepeerd en configureerbaar) wordt niet bijgewerkt wanneer de voorraadstatus van het subproduct via REST API-POST `/rest/V1/inventory/source-items` wordt gewijzigd.

<u> Stappen om </u> te reproduceren:

1. Creeer een configureerbaar, gebundeld, en gegroepeerd product met één eenvoudig kindproduct voor elk.
1. Stel elke eenvoudige status van het onderliggende product in op **[!UICONTROL Out of Stock]** met behulp van de API-aanroep van `source-items` .
1. Controleer nu de voorraadstatus van het bovenliggende product.

<u> Verwachte resultaten </u>:

De status van het bovenliggende product is [!UICONTROL Out of Stock] .

<u> Ware resultaten </u>:

De status van het bovenliggende product is [!UICONTROL In Stock] .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
