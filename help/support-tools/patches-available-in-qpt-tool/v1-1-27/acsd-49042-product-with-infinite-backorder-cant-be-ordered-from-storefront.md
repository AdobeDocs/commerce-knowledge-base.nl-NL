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

De ACSD-49042-patch verhelpt het probleem waarbij een product met een oneindige backorder niet vanuit de winkel kan worden besteld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-49042. De kwestie is opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De fout treedt op wanneer een product met een oneindige backorder niet van de storefront kan worden bevolen.

<u>Stappen om te reproduceren</u>:

1. Stel de volgende configuratie-instellingen in:
   * **[!UICONTROL Display Out of Stock Products]** instellen op *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** instellen op *[!UICONTROL Allow Qty Below 0]*.
1. Een nieuwe toevoegen **[!DNL custom stock]** en **[!DNL custom source]**.
1. Een product toewijzen aan de **[!DNL custom source]** en zorg ervoor dat er een inventarisnummer voor is ingesteld (bijvoorbeeld: *10*).
1. Open op de productbewerkingspagina **[!UICONTROL Advanced Inventory]**. Stel de **[!UICONTROL minimum quantity]** in de kar (bijvoorbeeld: *160*). De hoeveelheid moet boven de voorraad liggen.
1. Ga naar de winkel en koop een product om een boeking te maken.
1. Wijzig de **[!UICONTROL product quantity]** tot *0*. Het cruciale punt is om het product op te slaan uit de **[!DNL Admin panel]** wanneer er een voorbehoud is.
1. Open de **[!UICONTROL product page]** op de winkel en probeer het product aan de kar toe te voegen.

<u>Verwachte resultaten</u>:

Het is mogelijk om het product aan het winkelwagentje toe te voegen omdat achterordes voor een hoeveelheid onder *0* zijn toegestaan.

<u>Werkelijke resultaten</u>:

Het product blijkt uit voorraad te zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
