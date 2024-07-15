---
title: "MDVA-32313 patch: products added to wishlist with wrong configuration"
description: De flard MDVA-32313 lost de kwestie op waar de configureerbare producten niet correct aan verlanglijst kunnen worden toegevoegd, omdat zij verkeerde configuraties wanneer zij aan verlanglijst worden toegevoegd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.2.
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-32313 patch: products added to wishlist with wrong configuration

De flard MDVA-32313 lost de kwestie op waar de configureerbare producten niet correct aan verlanglijst kunnen worden toegevoegd, omdat zij verkeerde configuraties wanneer zij aan verlanglijst worden toegevoegd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur 2.3.0

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.3.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Maak een klant.
1. Meld u aan bij de klantenaccount.
1. Navigeer aan de **Lijst van het Product** pagina.
1. Kies een configureerbaar product (Voorbeeld: *configureerbaar \_1*) en selecteer aangewezen kleur en grootteopties op de **Lijst van het Product** pagina (**open niet de productpagina.**).
1. Klik op het wenslijstpictogram van een ander configureerbaar product (Voorbeeld: *configureerbaar \_2*) op de zelfde pagina zonder enige kleur/grootteopties te selecteren.

<u> Verwachte resultaten </u>:

Het *configureerbare \_2* product wordt toegevoegd aan verlanglijst zonder geselecteerde opties, zoals verwacht.

<u> Ware resultaten </u>:

Het *configureerbare \_2* product dat aan de wenslijst met de configuratie van het *wordt toegevoegd configureerbare \_1* product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
