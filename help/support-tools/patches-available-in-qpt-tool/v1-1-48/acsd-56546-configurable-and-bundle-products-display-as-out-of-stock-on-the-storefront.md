---
title: "ACSD-56546: configureerbare en bundelproducten worden weergegeven als producten die niet in voorraad zijn in de winkel"
description: Pas de ACSD-56546-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de configureerbare en bundelproducten als uit voorraad op de winkel worden weergegeven wanneer de *[!UICONTROL Display Out of Stock Products]* De configuratieoptie is uitgeschakeld.
feature: Storefront, Products
role: Admin, Developer
exl-id: 488e2c69-442f-45e1-aa8f-71d9c0a93950
source-git-commit: 031d5cad6727bac61c88f21fa7c84e0d2a6df331
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546: configureerbare en bundelproducten worden weergegeven als producten die niet in voorraad zijn in de winkel

De ACSD-56546-patch verhelpt het probleem waarbij de configureerbare en bundelproducten worden weergegeven als producten die niet in voorraad zijn in de winkel. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 is geïnstalleerd. De patch-id is ACSD-56546. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Configureerbare en bundelproducten worden weergegeven als onvoorraad op de winkel wanneer *[!UICONTROL Display Out of Stock Products]* is uitgeschakeld.

<u>Stappen om te reproduceren</u>:

1. Stel de **[!UICONTROL Display Out of Stock Products]** optie voor *Nee*.
1. Maak een website, winkel en voorvertoning.
1. Maak een bron en een voorraad en wijs deze vervolgens toe aan de tweede website.
1. Een *configureerbaar product* met twee kinderproducten. Wijs zowel de onderliggende producten aan beide bronnen als aan beide websites toe.
1. Het eerste onderliggende product bijwerken *qty=0* in beide bronnen.
1. Werk het tweede onderliggende product bij en schakel het uit op de tweede website.
1. Voer een volledige redex uit.
1. Controleer de categorie die het configureerbare product op de tweede website bevat.

<u>Verwachte resultaten</u>:

De uit-van-voorraad configureerbare producten zijn niet zichtbaar op de winkel.

<u>Werkelijke resultaten</u>:

De uit-van-voorraad configureerbare producten zijn zichtbaar op de winkel zelfs wanneer *[!UICONTROL Display Out of Stock Products]* is uitgeschakeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
