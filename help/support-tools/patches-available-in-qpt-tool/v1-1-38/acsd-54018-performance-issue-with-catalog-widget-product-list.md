---
title: 'ACSD-54018: Prestatieprobleem met de productlijst van de widget voor de catalogus'
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

De ACSD-54018-patch verhelpt het probleem waarbij de pagina langzaam wordt geladen wanneer een productlijst van een cataloguswidget met voorwaarde en kenmerktype Boolean wordt toegevoegd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 is geïnstalleerd. De patch-id is ACSD-54018. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De pagina wordt traag geladen wanneer een productlijst van een cataloguswidget met voorwaarde en kenmerktype boolean wordt toegevoegd.

<u>Stappen om te reproduceren</u>:

1. Produceer 100 k producten.
1. Maak een bool-kenmerk met het bereik ingesteld op [!UICONTROL Store View].
1. Kenmerk toewijzen aan alle kenmerksets.
   * Kenmerkwaarde toewijzen *Ja* op alle producten.
1. Ga nu naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en selecteert u alle 100k-producten.
   * Kies **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * Stel het bool-kenmerk in op *Ja* en sla deze op.
   * Als u zich bij deze stap hebt afgemeld, controleert u de *Notities*.
1. Naar CLI gaan en uitvoeren `php bin/magento queue:con:start product_action_attribute.update`.
   * Zorg ervoor dat de kenmerken voor alle producten zijn bijgewerkt.
1. Ga nu naar **[!UICONTROL Content]** > **[!UICONTROL Pages]** en maak een nieuwe pagina.
1. Openen **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. Kies *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. De voorwaarde instellen *[!UICONTROL Created attribute]* tot *[!UICONTROL Yes]* en sla deze op.
1. Ga naar de voorkant en open de gemaakte pagina.
1. Schakel de cache van de volledige pagina uit en blokkeer de HTML-cache.
1. Controleer de laadsnelheid van de pagina.
1. Laad de pagina een paar keer opnieuw en bereken de gemiddelde laadtijd.

<u>Verwachte resultaten</u>:

De pagina wordt snel geladen.

<u>Werkelijke resultaten</u>:

Het laden van de pagina duurt 5-10 seconden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
