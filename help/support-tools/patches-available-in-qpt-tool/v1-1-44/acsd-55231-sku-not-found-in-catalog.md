---
title: 'ACSD-55231: SKU heeft geen fout aangetroffen tijdens het gebruik van de functie voor snelle bestellingen.'
description: Pas de ACSD-55231-patch toe om het Adobe Commerce-probleem op te lossen, waarbij *'De SKU is niet gevonden in de catalogus'*-fout tijdens het toevoegen van een product aan het winkelwagentje met behulp van de functie voor snelle bestelling.
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: 463c2c07-39ec-4b03-81f7-ec2f71f5af76
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-55231: SKU niet gevonden fout tijdens gebruik van snelle-ordefunctionaliteit

De ACSD-55231-patch verhelpt het probleem waar u terecht komt *&#39;De SKU is niet gevonden in de catalogus&#39;* fout bij het toevoegen van een product aan de winkelwagentje met behulp van de functie voor snelle bestelling. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 is geïnstalleerd. De patch-id is ACSD-55231. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aan de slag *&#39;the SKU was not found in the catalog&#39;* fout bij het zoeken naar producten die u aan het winkelwagentje wilt toevoegen met behulp van de functie voor snelle bestelling.

<u>Stappen om te reproduceren</u>:

1. Installeer Adobe Commerce met B2B-modules.
1. Navigeren naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** en instellen:
   * **[!UICONTROL Enable company]**: *Ja*
   * **[!UICONTROL Enable Shared Catalog]**: *Ja*
   * **[!UICONTROL Enable Quick Order]**: *Ja*
1. Sla de bovenstaande configuratie op.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** en maakt u een nieuwe gedeelde catalogus.
1. Navigeren naar **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** en een nieuwe klant te maken:
   * Kies in het groepsveld de onlangs gemaakte gedeelde catalogus en stel deze in *[!UICONTROL Allow remote shopping assistance]* tot *Ja*.
1. Een eenvoudig product genereren met SKU *p12*, koppelen aan de categorie *c1* en kies vervolgens voor de nieuw gemaakte gedeelde catalogus in het dialoogvenster [!UICONTROL Product in Shared Catalog] sectie.
1. Uitvoeren:

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Vernieuw de beheerpagina.
1. Navigeren naar **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** en bewerk de eerder gemaakte klant.
1. Klik op **[!UICONTROL Login as customer]**.
1. Ga naar **[!UICONTROL Quick order]**.
1. Zoeken in de *p12* SKU en klik op de **[!UICONTROL Product Suggestion]**.
1. Voeg dit product toe aan winkelwagentje en plaats de bestelling.
1. Terug naar **[!UICONTROL Quick Order]**, zoeken naar SKU *p12* nogmaals, en klik op **[!UICONTROL Product Suggestion]**.

<u>Verwachte resultaten</u>:

U kunt het product met de functie voor snelle bestellingen aan het winkelwagentje toevoegen.

<u>Werkelijke resultaten</u>:

U kunt het product niet aan het winkelwagentje toevoegen met de functie voor snelle bestelling en u kunt *&#39;De SKU is niet gevonden in de catalogus&#39;* fout bij het zoeken naar product-SKU.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
