---
title: "ACSD-49042: Product met een oneindige backorder kan niet van opslagront worden bevolen"
description: Pas de ACSD-49042-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een product met een oneindige backorder niet van de winkel kan worden besteld.
exl-id: b9227296-f300-447c-a241-30ccc0691c9a
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042: product met oneindige backorder kan niet van opslagront worden bevolen

De ACSD-49042-patch verhelpt het probleem waarbij een product met een oneindige backorder niet vanuit de winkel kan worden besteld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-49042. De kwestie is opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De fout treedt op wanneer een product met een oneindige backorder niet van de storefront kan worden bevolen.

<u> Stappen om </u> te reproduceren:

1. Stel de volgende configuratie-instellingen in:
   * **[!UICONTROL Display Out of Stock Products]** ingesteld op *[!UICONTROL Yes]* .
   * **[!UICONTROL Backorders]** ingesteld op *[!UICONTROL Allow Qty Below 0]* .
1. Voeg een nieuwe **[!DNL custom stock]** en **[!DNL custom source]** toe.
1. Wijs een product aan **[!DNL custom source]** toe en zorg ervoor dat er een inventarisaantal voor het wordt geplaatst (bijvoorbeeld: *10*).
1. Open **[!UICONTROL Advanced Inventory]** op de productbewerkingspagina. Plaats **[!UICONTROL minimum quantity]** in de kar, (bijvoorbeeld: *160*). De hoeveelheid moet boven de voorraad liggen.
1. Ga naar de winkel en koop een product om een boeking te maken.
1. Verander **[!UICONTROL product quantity]** in *0*. Het kritieke punt is om het product van **[!DNL Admin panel]** te bewaren wanneer er een reserve is.
1. Open **[!UICONTROL product page]** op de winkel en probeer het product aan de winkelwagentje toe te voegen.

<u> Verwachte resultaten </u>:

Het is mogelijk om het product aan de kar toe te voegen omdat de achterorden voor een hoeveelheid onder *0* worden toegestaan.

<u> Ware resultaten </u>:

Het product blijkt uit voorraad te zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
