---
title: "ACSD-55238: Bewaar de lege meta-beschrijving van het product"
description: Pas de ACSD-55238-patch toe om het Adobe Commerce-probleem op te lossen waarbij een productbeschrijving met HTML-code die is gegenereerd door [!DNL Page Builder] of er wordt altijd een andere HTML-editor weergegeven in de metabeschrijving en er is geen manier om deze in te stellen op leeg.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 250026c3-925d-4a62-9855-d892c86d3d24
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-55238: De lege productmeta-beschrijving opslaan

De ACSD-55238-patch verhelpt het probleem dat een productbeschrijving met door een HTML-editor gegenereerde HTML-code altijd wordt weergegeven in de metabeschrijving. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 is geïnstalleerd. De patch-id is ACSD-55238. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een productbeschrijving met HTML-code die is gegenereerd door [!DNL Page Builder] of er wordt altijd een andere HTML-editor weergegeven in de metabeschrijving en er is geen manier om deze in te stellen op leeg.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** en maak een nieuw blok met alle inhoud.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** en maak een nieuw product. Stel de metabeschrijving in op leeg.
1. Voeg het hierboven gemaakte blok toe met *[!DNL Page Builder]* in de *[!UICONTROL Content]* en sla het product op.
1. Open het product op de winkel en controleer het documentelement `meta name = "description"`.

<u>Verwachte resultaten</u>:

De beschrijving van de meta is leeg.

<u>Werkelijke resultaten</u>:

Wanneer een product een blok in zijn beschrijving heeft, wordt het gebruikt voor de productbeschrijving van meta.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
