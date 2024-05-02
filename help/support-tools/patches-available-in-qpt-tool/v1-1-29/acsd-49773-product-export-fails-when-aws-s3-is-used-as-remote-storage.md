---
title: 'ACSD-49773: Exporteren van producten mislukt wanneer AWS S3 wordt gebruikt als externe opslag'
description: Pas de ACSD-49773-patch toe om het Adobe Commerce-probleem op te lossen waarbij het exporteren van het product mislukt wanneer AWS S3 wordt gebruikt als externe opslag.
exl-id: 5ef853c3-8080-4403-836b-6fff93ec71c6
feature: Data Import/Export, Iaas, Products, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-49773: Het exporteren van producten mislukt wanneer AWS S3 wordt gebruikt als externe opslag

De ACSD-49773-patch verhelpt het probleem waarbij het exporteren van een product mislukt wanneer AWS S3 wordt gebruikt als externe opslag. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-49773. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het exporteren van het product mislukt wanneer AWS S3 wordt gebruikt als externe opslag.

<u>Stappen om te reproduceren</u>:

1. Een groot gegevensprofiel installeren.
1. Maak een AWS-account en configureer een S3-emmertje en een IAM-gebruiker.
1. Bijwerken `app/etc/env.php` met de configuraties.
1. Uitvoeren `bin/magento setup:upgrade`.
1. Ga naar back-end en voer een volledige productexport uit.
1. Controleer de status van het rijbericht van de `[queue_message_status]` tabel.
1. Controleer de systeemlogboeken.

<u>Verwachte resultaten</u>:

Het exporteren van het product wordt zonder fouten voltooid.

<u>Werkelijke resultaten</u>:

Er is een fout opgetreden tijdens het aanmelden bij de systeemlogboeken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
