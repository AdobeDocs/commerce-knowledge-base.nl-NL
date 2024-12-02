---
title: 'ACSD-54018: Prestatieprobleem met de productlijst van de widget voor catalogi'
description: Pas de ACSD-54018-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de pagina langzaam wordt geladen wanneer een productlijst van een cataloguswidget met voorwaarde- en kenmerktype Boolean wordt toegevoegd.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 9f20484d-58c7-49d8-87df-1eeb84bee6fe
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-54018: Prestatieprobleem met de productlijst van de widget voor catalogi

De ACSD-54018-patch verhelpt het probleem waarbij de pagina langzaam wordt geladen wanneer een productlijst van een cataloguswidget met voorwaarde en kenmerktype Boolean wordt toegevoegd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 wordt geïnstalleerd. De patch-id is ACSD-54018. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De pagina wordt traag geladen wanneer een productlijst van een cataloguswidget met voorwaarde en kenmerktype boolean wordt toegevoegd.

<u> Stappen om </u> te reproduceren:

1. Produceer 100 k producten.
1. Maak een bool-kenmerk met het bereik ingesteld op [!UICONTROL Store View] .
1. Kenmerk toewijzen aan alle kenmerksets.
   * Wijs de attributenwaarde *ja* aan alle producten toe.
1. Ga nu naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en selecteer alle 100k-producten.
   * Kies **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]** .
   * Plaats de bool attributen aan *ja* en bewaar het.
   * Als u op deze stap het programma opende, controleer de *Nota&#39;s*.
1. Ga naar CLI en voer `php bin/magento queue:con:start product_action_attribute.update` uit.
   * Zorg ervoor dat de kenmerken voor alle producten zijn bijgewerkt.
1. Ga nu naar **[!UICONTROL Content]** > **[!UICONTROL Pages]** en maak een nieuwe pagina.
1. Open **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]** .
1. Kies *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]* .
1. Stel de voorwaarde *[!UICONTROL Created attribute]* in op *[!UICONTROL Yes]* en sla deze op.
1. Ga naar de voorkant en open de gemaakte pagina.
1. Schakel de cache van de volledige pagina uit en blokkeer de HTML-cache.
1. Controleer de laadsnelheid van de pagina.
1. Laad de pagina een paar keer opnieuw en bereken de gemiddelde laadtijd.

<u> Verwachte resultaten </u>:

De pagina wordt snel geladen.

<u> Ware resultaten </u>:

Het laden van de pagina duurt 5-10 seconden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
