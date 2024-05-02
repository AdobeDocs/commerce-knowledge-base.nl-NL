---
title: "ACSD-52399: Product met een verkoopbare hoeveelheid 0 in voorraad"
description: Pas de ACSD-52399-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de configureerbare productoptie met een verkoopbare hoeveelheid van 0 *In Stock* op de productpagina wordt weergegeven.
feature: Products, Configuration
role: Admin, Developer
exl-id: 3c9e6edd-f7ce-492e-b74f-68354d8e2633
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52399: product met verkoopbare hoeveelheid 0 in voorraad

De ACSD-52399-patch verhelpt het probleem waarbij de configureerbare productoptie met een verkoopbare hoeveelheid van nul (0) wordt weergegeven *In voorraad* op de productpagina. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-52399. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Configureerbare productoptie met een verkoopbare hoeveelheid van nul (0) toont *In voorraad* op de productpagina.

<u>Stappen om te reproduceren</u>:

1. Maak een configureerbaar product met de optie 0 (verkoopbaar) product.
1. Ga naar de productpagina op de winkel en selecteer het configureerbare product om een variatie/configuratie te controleren.
1. Selecteren **[!UICONTROL Add to Cart]**.

<u>Verwachte resultaten</u>:

*[!UICONTROL Add to Cart]* de knop is niet beschikbaar wanneer u *Uit voorraad* productconfiguratie.

<u>Werkelijke resultaten</u>:

Configureerbare variaties zijn beschikbaar op de winkelserver en u kunt ze selecteren en aan de winkelwagentje toevoegen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
