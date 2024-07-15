---
title: "MDVA-34102: inconsistente verkoopbare hoeveelheid"
description: De patch MDVA-34102 lost het probleem op waarbij de hoeveelheid standaardvoorraad nul is voor uitgeschakelde producten op het Productraster en Productpagina's bewerken in Admin. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is MDVA-34102. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.
exl-id: cb1d4689-c122-4afd-8597-b2627027aaf3
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-34102: inconsistente verkoopbare hoeveelheid

De patch MDVA-34102 lost het probleem op waarbij de hoeveelheid standaardvoorraad nul is voor uitgeschakelde producten op het Productraster en Productpagina&#39;s bewerken in Admin. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 geïnstalleerd is. De patch-id is MDVA-34102. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Twee websites instellen met winkels en winkelweergaven.
1. Maak een extra bron en voorraad.
1. Voeg een eenvoudig product toe:
   * Plaats **laat Product** toe = *Nr*.
   * Wijs twee bronnen met **Status van het Punt van Source** toe = *In Voorraad* met een hoeveelheid groter dan nul (Voorbeeld: **standaardvoorraad** = *123* en **voorraad van het VK** = *123*).
1. Sla het product op.
1. Controleer het **Aanpasbare Aantal van het Product** lusje.

<u> Verwachte resultaten </u>:

Zowel de standaardvoorraad als de voorraad van het VK = *123.*

De hoeveelheid standaardvoorraad wordt correct weergegeven voor uitgeschakelde producten op de pagina&#39;s Productraster en Product bewerken in Admin.

<u> Ware resultaten </u>:

De standaardvoorraad = *0* en de voorraad van het VK = *123.*

De hoeveelheid standaardvoorraad is nul voor uitgeschakelde producten op het productraster en de pagina&#39;s Product bewerken in de Admin.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
