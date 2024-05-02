---
title: "MDVA-34330: Orders niet gefilterd volgens tijdzone admin"
description: De MDVA-34330-patch lost het probleem op waarbij orders niet worden gefilterd volgens de tijdzone van de beheerder. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 is geïnstalleerd. De patch-id is MDVA-34330. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: cb369ee3-60b0-4317-a448-0c4ed64f2816
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# MDVA-34330: Orders niet gefilterd volgens tijdzone admin

De MDVA-34330-patch lost het probleem op waarbij orders niet worden gefilterd volgens de tijdzone van de beheerder. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 is geïnstalleerd. De patch-id is MDVA-34330. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatietypen) 2.3.1 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Orders worden niet gefilterd volgens de tijdzone van het beheerder.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > Instellingen > **Configuratie** > **Algemeen** en stelt de **Tijdzone** tot *Eastern Standard Time (Amerika/New_York)*
1. Een nieuwe bestelling plaatsen na 00:00 UTC
1. Ga naar **Verkoop** > **Orders** en filteren op de datum van vandaag


<u>Verwachte resultaten</u>:

De volgorde die vandaag wordt geplaatst na 00:00 UTC is zichtbaar in gefilterde resultaten.

<u>Werkelijke resultaten</u>:

De volgorde ontbreekt in gefilterde resultaten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
