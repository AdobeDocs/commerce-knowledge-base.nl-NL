---
title: 'ACSD-56023: inhoud van widget wordt niet bijgewerkt op de CMS-pagina'
description: Pas de ACSD-56023-patch toe om het Adobe Commerce-probleem op te lossen waarbij de widgetinhoud niet wordt bijgewerkt op de CMS-pagina
feature: CMS
role: Admin, Developer
exl-id: 2ff33b1c-ae92-4c59-83d2-e252bf543bab
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-56023: Widget-inhoud wordt niet bijgewerkt op de CMS-pagina

De ACSD-56023-patch verhelpt het probleem waarbij de widgetinhoud niet wordt bijgewerkt op de CMS-pagina. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 is geïnstalleerd. De patch-id is ACSD-56023. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Widget-inhoud wordt niet bijgewerkt op de CMS-pagina.

<u>Stappen om te reproduceren</u>:

1. Maak een paar producten.
1. Maak de nieuwe CMS-pagina en voeg een nieuwe widget producten toe aan de inhoud:

   ```
      {{widget type="Magento\Catalog\Block\Product\Widget\NewWidget" display_type="new_products" show_pager="1" products_per_page="5" products_count="10" template="product/widget/new/content/new_grid.phtml" page_var_name="pnetpm"}} 
   ```

1. Open de gemaakte pagina in de winkel. Zorg ervoor dat u de sjabloon in de cache plaatst.
1. Open vanuit de beheerder **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Elk product kiezen voor bewerken en schakelen **[!UICONTROL Set Product as New]** tot *Ja*.
1. Ga naar het gemaakte *CMS-pagina* weer in de winkel.

<u>Verwachte resultaten</u>:

De pagina bevat *Widget Nieuwe producten* met de producten.

<u>Werkelijke resultaten</u>:

De pagina bevat niet *Widget Nieuwe producten* en de nieuwe producten worden niet weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
