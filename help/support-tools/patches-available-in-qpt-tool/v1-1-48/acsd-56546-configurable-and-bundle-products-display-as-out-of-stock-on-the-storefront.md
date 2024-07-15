---
title: "ACSD-56546: configureerbare en bundelproducten worden weergegeven als producten die niet in voorraad zijn in de winkel"
description: Pas ACSD-56546 flard toe om de kwestie van Adobe Commerce te bevestigen waar de configureerbare en bundelproducten als uit voorraad op de opslagplaats tonen wanneer de * [!UICONTROL Display Out of Stock Products]* configuratieoptie wordt onbruikbaar gemaakt.
feature: Storefront, Products
role: Admin, Developer
exl-id: 488e2c69-442f-45e1-aa8f-71d9c0a93950
source-git-commit: 031d5cad6727bac61c88f21fa7c84e0d2a6df331
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546: configureerbare en bundelproducten worden weergegeven als producten die niet in voorraad zijn in de winkel

De ACSD-56546-patch verhelpt het probleem waarbij de configureerbare en bundelproducten worden weergegeven als producten die niet in voorraad zijn in de winkel. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-56546. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Configureerbare en bundelproducten worden als out of stock in de winkel weergegeven wanneer de optie *[!UICONTROL Display Out of Stock Products]* is uitgeschakeld.

<u> Stappen om </u> te reproduceren:

1. Plaats de **[!UICONTROL Display Out of Stock Products]** optie aan *Nr*.
1. Maak een website, winkel en voorvertoning.
1. Maak een bron en een voorraad en wijs deze vervolgens toe aan de tweede website.
1. Creeer a *configureerbaar product* met twee kindproducten. Wijs zowel de onderliggende producten aan beide bronnen als aan beide websites toe.
1. Werk het eerste kindproduct bij om *qty=0* in beide bronnen te hebben.
1. Werk het tweede onderliggende product bij en schakel het uit op de tweede website.
1. Voer een volledige redex uit.
1. Controleer de categorie die het configureerbare product op de tweede website bevat.

<u> Verwachte resultaten </u>:

De uit-van-voorraad configureerbare producten zijn niet zichtbaar op de winkel.

<u> Ware resultaten </u>:

De configureerbare producten uit de voorraad zijn zichtbaar op de winkel, zelfs als de optie *[!UICONTROL Display Out of Stock Products]* is uitgeschakeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
