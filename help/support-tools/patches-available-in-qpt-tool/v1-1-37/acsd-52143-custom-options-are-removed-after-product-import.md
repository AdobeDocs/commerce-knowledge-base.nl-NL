---
title: 'ACSD-52143: aangepaste opties worden verwijderd na het importeren van het product'
description: Pas de ACSD-52143-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de aanpassingsopties worden verwijderd nadat het product is geïmporteerd.
feature: Data Import/Export
role: Admin, Developer
exl-id: 7dde1efe-37a3-443f-9ce1-82cf1b3d9da7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-52143: na het importeren van het product worden de aangepaste opties verwijderd

De ACSD-52143-patch verhelpt het probleem waarbij de aangepaste opties worden verwijderd na het importeren van het product. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 is geïnstalleerd. De patch-id is ACSD-52143. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De aangepaste opties worden verwijderd nadat het product is geïmporteerd.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Store]** > **[!UICONTROL All Stores]** en stel een instantie van meerdere winkels in (één website met twee winkelweergaven).
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en twee producten maken met [!UICONTROL Customizable Options].
1. Voeg in elk product een [!UICONTROL Customizable Option].
1. Schakel over naar de tweede winkelweergave en wijzig de productnaam op elk product.
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** en exporteer de twee producten die u hebt gemaakt.
1. Download het CSV-bestand.
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** en importeer het bestand opnieuw.
1. Controleer beide producten.

<u>Verwachte resultaten</u>:

De aangepaste opties worden niet verwijderd nadat het product is geïmporteerd.

<u>Werkelijke resultaten</u>:

De douaneopties worden verwijderd na de invoer van het product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
