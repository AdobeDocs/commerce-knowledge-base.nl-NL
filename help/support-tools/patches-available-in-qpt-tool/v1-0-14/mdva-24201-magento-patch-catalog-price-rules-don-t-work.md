---
title: "MDVA-24201: Catalogusprijsregels werken niet"
description: De patch MDVA-24201 lost het probleem op waar de actieve prijsregels voor catalogi in de database niet van toepassing zijn op de frontend.
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201: Catalogusprijsregels werken niet

De patch MDVA-24201 lost het probleem op waar de actieve prijsregels voor catalogi in de database niet van toepassing zijn op de frontend.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce versie 2.3.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.3.3

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur en Adobe Commerce op-gebouw 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Vereiste </u>:

Installeer een nieuw exemplaar van het Magento met steekproefgegevens.

<u> Stappen om </u> te reproduceren:

1. Login aan **Admin paneel** > **Marketing** > **de Regel van de Prijs van de Catalogus** > **voegt Nieuwe Regel** toe, maak de volgende montages:
   1. Plaats de **Naam van de Regel**.
   1. Plaats **Actief** = *Nr.*
   1. Plaats Voorwaarden: **Categorie** = *4*. (Voorbeeld: tags)
   1. Handelingen instellen:
      1. Plaats **van toepassing is als**   **percentage origineel**.
      1. Plaats **Bedrag van de Korting** = *10*.
      1. Sla het bestand op en ga verder met het bewerken.
   1. Klik op **Nieuwe Update van het Programma**:
      * Plaats de **Naam van de Regel**.
      * Plaats **Actief** = *ja*.
      * Opslaan.
1. Ga naar de achtergrond en voer uit:

   `php    bin/magento cron:run`

<u> Verwachte resultaten </u>:

De prijzen van de producten van categorie 4 &quot;Bags&quot; moeten worden verlaagd met 10% van de oorspronkelijke prijs, zoals bepaald in de regel inzake catalogusprijzen, zoals verwacht.

<u> Ware resultaten </u>:

Er vinden geen prijswijzigingen plaats, ook al is de regel voor catalogusprijzen actief.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
