---
title: "MDVA-34192 patch: can't modify customer date in certain format"
description: De MDVA-34192-patch verhelpt het probleem waarbij het onmogelijk is de geboortedatum van de klant te wijzigen of op te geven in de indeling dd/mm/jjjj. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-34192 patch: can&#39;t modify customer date in certain format

De MDVA-34192-patch verhelpt het probleem waarbij het onmogelijk is de geboortedatum van de klant te wijzigen of op te geven in de indeling dd/mm/jjjj. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.3.5-p1

**Compatibel met de versies van Adobe Commerce:** 2.3.4-2.3.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De patch lost verschillende problemen op. Hieronder vindt u de beschrijving en stappen die u voor een van deze componenten wilt reproduceren.

Het productrasterfilter werkt niet correct wanneer we filteren met het kenmerk custom date en de landinstelling van de beheerder-gebruiker is en\_GB.

<u> Stappen om te reproduceren:</u>:

1. Creeer een admin gebruiker de waarvan **Plaats van de Interface** aan *Engels (Verenigd Koninkrijk)* wordt geplaatst.
1. Maak een datumkenmerk met de volgende configuratie:
   * **Type van Invoer van de Catalogus voor de Eigenaar van de Opslag**: *Datum*
   * **Gebruik in de Opties van de Filter**: *ja*
   * **voeg aan de Opties van de Kolom toe**: *ja*
1. Wijs het kenmerk toe aan een kenmerkset.
1. Ga naar de productbewerkingspagina, selecteer een datum voor het nieuwe kenmerk met de datumkiezer en sla deze op.
1. Probeer het productraster te filteren met het nieuwe datumkenmerk.

<u> Verwacht resultaat:</u>:

Het filter Product werkt correct voor een attribuut van de douanedatum wanneer de admin gebruikersscène en \_GB is.

<u> Ware resultaat:</u>:

Het productfilter werkt niet correct voor een aangepast datumkenmerk wanneer de landinstelling van de gebruiker voor het beheer en\_GB is.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
