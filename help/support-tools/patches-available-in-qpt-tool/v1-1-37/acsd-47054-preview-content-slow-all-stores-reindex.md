---
title: 'ACSD-47054: Voorvertoning van inhoud traag als alle opslagherdex'
description: Pas de ACSD-47054-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de voorvertoningspagina traag wordt geladen omdat alle winkels opnieuw zijn geindexeerd.
feature: Page Content
role: Admin, Developer
exl-id: 4dc61f78-7038-48ab-a2d3-9b05cf0c9b5c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47054: Voorvertoning van inhoud traag als alle opslagherdex

De ACSD-47054-patch verhelpt het probleem waarbij het langer duurt om een voorvertoning van de inhoudstaging te laden als er veel opslagruimten zijn. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 is geïnstalleerd. De patch-id is ACSD-47054. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden): 2.4.2-p2, 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het laden van de voorvertoningspagina duurt lang omdat alle winkels opnieuw zijn gecompileerd.

<u>Stappen om te reproduceren</u>:

1. Ga naar Commerce Admin.
1. Maak een geplande update.
1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Dashboard]**.
1. Geef een voorvertoning weer van de geplande update.
1. Open een categorie.

<u>Verwachte resultaten</u>:

De voorvertoningspagina wordt binnen een aanvaardbare tijd geladen.

<u>Werkelijke resultaten</u>:

Het duurt erg lang om een voorvertoning van de inhoudstaging weer te geven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
