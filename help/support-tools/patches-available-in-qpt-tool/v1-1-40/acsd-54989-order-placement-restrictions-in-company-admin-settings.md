---
title: '"ACSD-54989: Bedrijfsbeheerder kan niet bestellen wanneer [!UICONTROL Enable Purchase Orders] ingesteld op Ja en [!UICONTROL Purchase Order] ingesteld op Nee'''
description: Pas de ACSD-54989-patch toe om het Adobe Commerce-probleem op te lossen, waarbij bedrijfsbeheerders geen orders kunnen plaatsen als [!UICONTROL Enable Purchase Orders] is ingesteld op Ja en [!UICONTROL Purchase Order] is ingesteld op Nee.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: c2850409-d310-4681-80ec-af8ba347854c
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54989: Bedrijfsbeheerder kan niet bestellen wanneer *[!UICONTROL Enable Purchase Orders]* instellen op *Ja* en *[!UICONTROL Purchase Order]* instellen op *Nee*

De ACSD-54989-patch verhelpt het probleem waarbij geen orders kunnen worden geplaatst als **[!UICONTROL Enable Purchase Orders]** instellen op *Ja* en **[!UICONTROL Purchase Order]** instellen op *Nee*. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 is geïnstalleerd. De patch-id is ACSD-54989. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bedrijfsbeheerders kunnen geen orders plaatsen wanneer **[!UICONTROL Enable Purchase Orders]** is ingesteld op *Ja* en **Inkooporder** instellen op *Nee*.

<u>Vereisten</u>:

Installeren [!DNL B2B] modules.

<u>Stappen om te reproduceren</u>:

1. Bedrijf inschakelen en vertrekken [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *Nee*.
1. Maak een eenvoudig product met een prijs van 100.
1. Maak een nieuw bedrijf via de beheerder.
1. Set [!UICONTROL **Aankooporders inschakelen**] tot *Ja*.
1. Meld u aan als bedrijfsbeheerder op de winkel.
1. Voeg het gemaakte eenvoudige product toe aan het winkelwagentje.
1. Ga naar de pagina Afrekenen en klik op **[!UICONTROL Place Order]** om de aankoop te voltooien.

<u>Verwachte resultaten</u>:

U kunt een bestelling plaatsen.

<u>Werkelijke resultaten</u>:

De **[!UICONTROL My Account]** pagina wordt geopend en de volgorde wordt niet geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
