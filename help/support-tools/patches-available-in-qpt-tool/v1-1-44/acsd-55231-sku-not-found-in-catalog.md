---
title: 'ACSD-55231: SKU niet gevonden fout tijdens gebruik van snelle-ordefunctionaliteit'
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

De markering ACSD-55231 verhelpt de kwestie waar u *&quot;SKU werd niet gevonden in de catalogus&quot;* fout wanneer het proberen om een product aan het karretje toe te voegen gebruikend snelle ordefunctionaliteit. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 wordt geïnstalleerd. De patch-id is ACSD-55231. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het krijgen *&quot;SKU werd niet gevonden in de catalogus&#39;* fout toen het zoeken naar producten om aan de kar toe te voegen gebruikend snelle ordefunctionaliteit.

<u> Stappen om </u> te reproduceren:

1. Installeer Adobe Commerce met B2B-modules.
1. Navigeer naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** en stel in:
   * **[!UICONTROL Enable company]**: *ja*
   * **[!UICONTROL Enable Shared Catalog]**: *ja*
   * **[!UICONTROL Enable Quick Order]**: *ja*
1. Sla de bovenstaande configuratie op.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** en maak een nieuwe gedeelde catalogus.
1. Navigeer naar **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** en maak een nieuwe klant:
   * Op het groepsgebied, kies onlangs gecreeerd gedeelde catalogus en reeks *[!UICONTROL Allow remote shopping assistance]* aan *ja*.
1. Produceer een eenvoudig product met SKU *p12*, associeer het met de categorie *c1*, en kies dan voor de pas gecreëerde gedeelde catalogus in de [!UICONTROL Product in Shared Catalog] sectie.
1. Uitvoeren:

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Vernieuw de beheerpagina.
1. Navigeer naar **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** en bewerk de eerder gemaakte klant.
1. Klik op **[!UICONTROL Login as customer]**.
1. Ga naar **[!UICONTROL Quick order]** .
1. Onderzoek *p12* SKU en klik op **[!UICONTROL Product Suggestion]**.
1. Voeg dit product toe aan winkelwagentje en plaats de bestelling.
1. Terugkeer aan **[!UICONTROL Quick Order]**, zoek opnieuw naar SKU *p12*, en klik op **[!UICONTROL Product Suggestion]**.

<u> Verwachte resultaten </u>:

U kunt het product met de functie voor snelle bestellingen aan het winkelwagentje toevoegen.

<u> Ware resultaten </u>:

U kunt niet het product aan de kar toevoegen gebruikend de snelle ordefunctionaliteit en krijgen *&quot;SKU werd niet gevonden in de catalogus&#39;* fout toen het zoeken naar product SKU.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
