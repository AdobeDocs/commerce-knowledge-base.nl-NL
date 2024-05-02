---
title: 'ACSD-54067: Productvideo wordt niet afgespeeld op een mobiel apparaat'
description: Pas de ACSD-54067-patch toe om het Adobe Commerce-probleem op te lossen waarbij een productvideo niet op een mobiel apparaat wordt afgespeeld.
feature: Media, Products
role: Admin, Developer
exl-id: 369650ef-bcce-47c5-bbfe-39f3c2b1d73f
source-git-commit: 0795e3e0ba11002c8aff2794e16fa05f1c7e19c3
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-54067: productvideo wordt niet afgespeeld op een mobiel apparaat

De ACSD-54067-patch verhelpt het probleem waarbij een productvideo niet op een mobiel apparaat wordt afgespeeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 is geïnstalleerd. De patch-id is ACSD-54067. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een productvideo wordt niet afgespeeld op een mobiel apparaat.

<u>Stappen om te reproduceren</u>:

1. Adobe Commerce installeren.
1. Voer de opdracht uit:
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Ga naar **[!UICONTROL Admin product list]** pagina en filter op *[!UICONTROL SKU product_dynamic_120]*.
1. Open de productpagina en ga naar **[!UICONTROL Images and Videos]** > voeg een video toe > vul de URL in: https://vimeo.com/347119375 en sla op.
1. Ga naar de winkel en open de productpagina voor *[!UICONTROL product_dynamic_120]*.
1. De browser instellen op *mobiel apparaat* met een breedte *320 px* en vernieuwen.
1. Selecteer de video in de schuifregelaar van de galerie en klik om deze af te spelen.

<u>Verwachte resultaten</u>:

De productvideo wordt afgespeeld.

<u>Werkelijke resultaten</u>:

De productvideo speelt niet.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
