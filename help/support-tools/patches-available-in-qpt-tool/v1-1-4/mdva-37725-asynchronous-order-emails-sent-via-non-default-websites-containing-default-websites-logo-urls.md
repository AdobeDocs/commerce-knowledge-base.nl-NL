---
title: "MDVA-37725: E-mails die via niet-standaardsites worden verzonden, bevatten URL's van het standaardlogo van de site."
description: De patch MDVA-37725 verhelpt het probleem dat e-mails met asynchrone bestellingen worden verzonden via niet-standaard websites met logo-URL's van de standaardwebsite.
exl-id: c0d1b9a3-01bb-445b-b7da-f9be6952eaeb
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-37725: E-mails die via niet-standaardsites worden verzonden, bevatten standaard URL&#39;s van het logo van de site

>[!WARNING]
>
> De MDVA-37725-pleister is afgekeurd.

De patch MDVA-37725 verhelpt het probleem dat e-mails met asynchrone bestellingen worden verzonden via niet-standaard websites met logo-URL&#39;s van de standaardwebsite. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 is geïnstalleerd. De patch-id is MDVA-37725. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mails met asynchrone bestellingen worden verzonden via niet-standaard websites met de URL&#39;s van het logo van de standaardwebsite.

<u>Vereisten</u>:

1. De tweede website/store/store-view moet zijn gemaakt.
1. **Asynchroon verzenden** de configuratie moet van worden toegelaten **Winkels** > **Instellingen** > **Configuratie** > **Verkoop** > **Verkoope-mail** > **Algemene instellingen**.
1. **Winkelcode toevoegen aan URL&#39;s** configuratie is ingeschakeld voor de eenvoudige toegang tot de secundaire website vanaf **Winkels** > **Instellingen** > **Configuratie** > **URL-opties**.

<u>Stappen om te reproduceren</u>:

1. Plaats bestellingen in zowel de eerste als de tweede winkel.
1. Voer een uitsnede uit om de e-mails over verkopen te verzenden.
1. Controleer de e-mail van de tweede website.

<u>Verwachte resultaten</u>:

De URL van het logo van de e-mail bevat de URL van de tweede website.

<u>Werkelijke resultaten</u>:

De URL van het logo van de e-mail bevat de URL van de standaardwebsite.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
