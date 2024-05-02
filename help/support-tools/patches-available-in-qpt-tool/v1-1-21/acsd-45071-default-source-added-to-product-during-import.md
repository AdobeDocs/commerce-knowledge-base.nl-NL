---
title: 'ACSD-45071: standaardbron toegevoegd aan product tijdens importeren'
description: De ACSD-45071-patch lost het probleem op waarbij de standaardbron tijdens het importeren aan het product wordt toegevoegd. Deze patch is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 is geïnstalleerd. De patch-id is ACSD-45071. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 8d8dbb06-6133-4d7a-939a-8bf18caec81c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-45071: standaardbron toegevoegd aan product tijdens importeren

De ACSD-45071-patch lost het probleem op waarbij de standaardbron tijdens het importeren aan het product wordt toegevoegd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 is geïnstalleerd. De patch-id is ACSD-45071. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Nadat een product is geïmporteerd, wordt de standaardbron automatisch toegewezen aan het product, wordt de hoeveelheid ingesteld op nul en wordt de status ingesteld op voorraadverlies.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe bron.
1. Maak een nieuw bestand met de nieuwe bron.
1. Wijs op de productbewerkingspagina in Adobe Commerce Admin alleen de aangepaste voorraad toe, stel een aantal in en stel de voorraadstatus in op **[!UICONTROL In Stock]**.
1. Het product importeren via **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**.

<u>Verwachte resultaten</u>:

De standaardbron wordt niet automatisch toegewezen aan het product na het importeren.

<u>Werkelijke resultaten</u>:

De standaardbron wordt toegewezen aan het product na het importeren met de status &#39;out-of-stock&#39; en de hoeveelheid &#39;nul&#39;.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
