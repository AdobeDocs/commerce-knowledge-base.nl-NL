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

De patch MDVA-37725 verhelpt het probleem dat e-mails met asynchrone bestellingen worden verzonden via niet-standaard websites met logo-URL&#39;s van de standaardwebsite. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 geïnstalleerd is. De patch-id is MDVA-37725. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mails met asynchrone bestellingen worden verzonden via niet-standaard websites met de URL&#39;s van het logo van de standaardwebsite.

<u> Eerste vereisten </u>:

1. De tweede website/store/store-view moet zijn gemaakt.
1. **Asynchrone Verzendende** configuratie moet van **Opslag** worden toegelaten > **Montages** > **Configuratie** > **Verkoop** > **E-mail van de Verkoop** > **Algemene Montages**.
1. **voeg de Code van de Opslag aan URLs** configuratie toe wordt aangezet voor de gemakkelijke toegang tot van de secundaire website van **Opslag** > **Montages** > **Configuratie** > **Opties URL**.

<u> Stappen om </u> te reproduceren:

1. Plaats bestellingen in zowel de eerste als de tweede winkel.
1. Voer een uitsnede uit om de e-mails over verkopen te verzenden.
1. Controleer de e-mail van de tweede website.

<u> Verwachte resultaten </u>:

De URL van het logo van de e-mail bevat de URL van de tweede website.

<u> Ware resultaten </u>:

De URL van het logo van de e-mail bevat de URL van de standaardwebsite.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
