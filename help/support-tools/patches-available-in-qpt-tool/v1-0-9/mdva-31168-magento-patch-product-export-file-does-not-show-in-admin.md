---
title: 'MDVA-31168 patch: Product export file does not show in Admin'
description: Met de MDVA-31168-patch wordt het probleem opgelost waarbij het CSV-bestand voor exporteren van het product niet voorkomt in de lijst met CSV-bestanden die kunnen worden geëxporteerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.2.
exl-id: 780a926b-2aea-47c2-8f95-907cc779bfa4
feature: Admin Workspace, Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# MDVA-31168 patch: Product export file does not show in Admin

Met de MDVA-31168-patch wordt het probleem opgelost waarbij het CSV-bestand voor exporteren van het product niet voorkomt in de lijst met CSV-bestanden die kunnen worden geëxporteerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op-gebouw 2.3.5-p2.

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur en Adobe Commerce op-gebouw 2.3.0 - 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Eerste vereisten </u>:

Installeer Adobe Commerce met voorbeeldgegevens.

<u> Stappen om te reproduceren:</u>

1. Creeer een downloadbaar product, en wijs het aan **categorie van Markeringen** toe.
1. Een exportbewerking starten voor alle producten.
1. Voer het volgende bevel van CLI uit:    ```php    bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000    ```

<u> Verwachte resultaten:</u>

Het CSV-bestand voor het exporteren van het product met alle producten wordt zoals verwacht weergegeven in de bestandenlijst in Admin.

<u> Ware resultaten:</u>

Het CSV-bestand voor het exporteren van het product met alle producten wordt niet weergegeven in de lijst in Admin, hoewel het bestand met alleen kopteksten wordt gegenereerd in de map `/var` op de server.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
