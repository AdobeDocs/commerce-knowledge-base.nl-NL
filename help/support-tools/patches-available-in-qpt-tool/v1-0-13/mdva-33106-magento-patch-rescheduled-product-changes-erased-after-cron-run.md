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

wordt uitgevoerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. In Commerce Admin, ga naar **Catalogus** > **Producten** en klik uitgeven. Merk de **waarde van de Prijs 0} {, bijvoorbeeld *9.99*.**
1. Klik **Nieuwe Update van het Programma** en vul details in:
   * De updatenaam is niet belangrijk.
   * Stel een datum in de toekomst in, +1 jaar voor de begin- en einddatum.
   * Plaats Prijs aan *1.99*.
   * Wijzigingen opslaan.
1. Ga naar het dashboard voor de inhoudstaging en selecteer de rasterweergave om te zien of de geplande overeenkomst hierboven overeenkomt.
1. Selecteer de actie Bewerken naast de geplande update. De gegevens moeten nog steeds overeenkomen.
1. Verander de geplande datum in iets dichter. Wijzig de waarde in + 1 week of + 1 maand in plaats van + 1 jaar vanaf nu.
1. Sla de wijzigingen op en controleer of de datums zijn bijgewerkt op het testdashboard.
1. Wacht tot een uitsnijdtaak is uitgevoerd.
1. Klik nogmaals op Bewerken in de geplande wijziging en controleer de prijs.

<u> Verwachte resultaten </u>:

De prijs is 1,99.

<u> Ware resultaten </u>:

De prijs is 9,99.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
