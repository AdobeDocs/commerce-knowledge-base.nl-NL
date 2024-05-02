---
title: 'Patch ''MDVA-33106: opnieuw geplande productwijzigingen gewist na uitvoering van de kroon'''
description: De MDVA-33106-patch verhelpt het probleem waarbij de opnieuw geplande productwijzigingen na de kroon worden gewist
exl-id: be32982c-796c-4069-ad70-37b5124ffb56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-33106-patch: opnieuw geplande productwijzigingen gewist na uitvoering van de cron

De MDVA-33106-patch verhelpt het probleem waarbij de opnieuw geplande productwijzigingen na de kroon worden gewist

```bash
bin/magento cron:run
```

wordt uitgevoerd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Ga in Commerce Admin naar **Catalogus** > **Producten** en klik op Bewerken. Let op: **Prijs** waarde, bijvoorbeeld *9,99*.
1. Klikken **Nieuwe update plannen** en vul details in:
   * De updatenaam is niet belangrijk.
   * Stel een datum in de toekomst in, +1 jaar voor de begin- en einddatum.
   * Prijs instellen op *1,99*.
   * Wijzigingen opslaan.
1. Ga naar het dashboard voor de inhoudstaging en selecteer de rasterweergave om te zien of de geplande overeenkomst hierboven overeenkomt.
1. Selecteer de actie Bewerken naast de geplande update. De gegevens moeten nog steeds overeenkomen.
1. Verander de geplande datum in iets dichter. Wijzig de waarde in + 1 week of + 1 maand in plaats van + 1 jaar vanaf nu.
1. Sla de wijzigingen op en controleer of de datums zijn bijgewerkt op het testdashboard.
1. Wacht tot een uitsnijdtaak is uitgevoerd.
1. Klik nogmaals op Bewerken in de geplande wijziging en controleer de prijs.

<u>Verwachte resultaten</u>:

De prijs is 1,99.

<u>Werkelijke resultaten</u>:

De prijs is 9,99.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
