---
title: 'ACSD-53824: implementatie mislukt bij installatie-upgrade'
description: Pas de ACSD-53824-patch toe om het Adobe Commerce-probleem op te lossen dat zich bij de upgrade van de installatie niet voordoet
feature: Attributes, Upgrade
role: Admin, Developer
exl-id: a071745f-967f-42c8-9e20-52b248e4fefa
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-53824: implementatie mislukt bij upgrade van installatie

De ACSD-53824-patch verhelpt het probleem waarbij de implementatie mislukt bij de upgrade van de installatie. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 is geïnstalleerd. De patch-id is ACSD-53824. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De plaatsing ontbreekt op opstellingsverbetering.

<u>Stappen om te reproduceren</u>:

1. De infrastructuur installeren met **[!DNL MariaDB]** op Galera Cluster.
1. Stel de `wsrep_max_ws_size` tot *2 GB*.
1. Installeer een nieuw Adobe Commerce-exemplaar.
1. De correcties genereren op basis van het gemiddelde prestatieprofiel:
   `php bin/magento setup:performance:generate-fixtures -s setup/performance-toolkit/profiles/ee/medium.xml`
1. Meer dan genereren **1200** kenmerken voor meerdere selecties.
1. Gebruik vervolgens de `Run setup: Upgrade` gebruiken.

<u>Verwachte resultaten</u>:

De `setup:upgrade` wordt zonder fouten voltooid.

<u>Werkelijke resultaten</u>:

De `setup:upgrade` mislukt met [!DNL MySQL] fouten:

`Allowed memory size of 6442450944 bytes exhausted in ../module-catalog/Setup/Patch/Data/UpdateMultiselectAttributesBackendTypes.php`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
