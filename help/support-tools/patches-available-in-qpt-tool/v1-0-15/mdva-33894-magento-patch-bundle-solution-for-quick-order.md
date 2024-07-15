---
title: 'MDVA-33894 patch: bundle solution for Quick Order'
description: De patch MDVA-33894 verhelpt meerdere problemen voor de functie Snelle bestelling, zoals het toevoegen en verwijderen van meerdere producten en de gevoeligheid van SKU-hoofdletters. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: d0b18e71-5f48-441e-a8b9-c459f3d34599
feature: Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-33894 patch: bundle solution for Quick Order

De patch MDVA-33894 verhelpt meerdere problemen voor de functie Snelle bestelling, zoals het toevoegen en verwijderen van meerdere producten en de gevoeligheid van SKU-hoofdletters. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.4.0

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur en Adobe Commerce op-gebouw 2.4.0-2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De MDVA-33894-patch is een bundeloplossing met oplossingen voor de volgende problemen:

* **Mijn Rekening** > **Orde door SKU** functionaliteit is gevoelig geval: als u geldige SKU maar het geval niet correct ingaat (in hoofdletters in plaats van in kleine letters etc.), veroorzaakt Adobe Commerce een fout.
* Wanneer een winkelier gebruik maakt van Snelle bestelling om meerdere producten aan zijn winkelwagentje toe te voegen en een product probeert te verwijderen, wordt het product niet verwijderd.
* Problemen met hoofdlettergevoeligheid bij het toevoegen van meerdere SKU&#39;s aan een bulkvolgorde.
* Cacheprobleem met de cache van de pagina Snelle bestelling met eerder ingevoerde SKU&#39;s.
* Hoeveelheid snelle bestelling wordt niet weergegeven in winkelwagentje.
* Overlappingen door SKU worden niet correct gevalideerd.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
