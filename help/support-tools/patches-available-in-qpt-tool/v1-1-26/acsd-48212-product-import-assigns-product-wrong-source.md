---
title: "ACSD-48212: product import wijst product aan verkeerde bron toe"
description: Pas de ACSD-48212-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het product door het importeren aan de verkeerde bron wordt toegewezen.
exl-id: b3426f62-f73a-4b76-8e0e-544a9133720f
feature: Admin Workspace, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48212: bij het importeren van producten wordt een product aan de verkeerde bron toegewezen

De ACSD-48212-patch verhelpt het probleem waarbij het product door het importeren aan de verkeerde bron wordt toegewezen. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 is geïnstalleerd. De patch-id is ACSD-48212. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het product wordt door het importeren aan de verkeerde bron toegewezen.

<u>Stappen om te reproduceren</u>:

1. Maak een secundaire inventarisbron.
1. Een product maken met alleen de standaardinventarisbron.
1. Het product exporteren.
1. Uitvoeren `bin/magento cron:run`.
1. Openen **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Selecteer het product in het raster.
1. Wijzig de toewijzing van het bestand met de *[!UICONTROL mass action]* -menu.
1. Uitvoeren `bin/magento cron:run`.
1. Wijs de secundaire bron toe gebruikend *[!UICONTROL mass action]* -menu.
1. Uitvoeren `bin/magento cron:run`.
1. Het product verwijderen met de opdracht *[!UICONTROL mass action]* -menu.
1. Uitvoeren `bin/magento cron:run`.
1. Importeer het product met behulp van de eerder geëxporteerde CSV.
1. Controleer de brontoewijzing.

<u>Verwachte resultaten</u>:

Het product wordt alleen aan de standaardbron toegewezen.

<u>Werkelijke resultaten</u>:

Het product wordt toegewezen aan zowel gebrek als secundaire bron.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
