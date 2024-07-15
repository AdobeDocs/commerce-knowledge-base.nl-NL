---
title: 'MDVA-41628: Beperkte beheerders krijgen toegang tot nieuwe bronnen'
description: Met de MDVA-41628-patch is het probleem verholpen waarbij gebruikers met beperkte bevoegdheden toegang hebben tot de nieuwe bronnen wanneer nieuwe modules worden toegevoegd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-41628. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 8f63ce9d-07b6-4d9d-a51b-b85b783b2adf
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-41628: Beperkte beheerders krijgen toegang tot nieuwe bronnen

Met de MDVA-41628-patch is het probleem verholpen waarbij gebruikers met beperkte bevoegdheden toegang hebben tot de nieuwe bronnen wanneer nieuwe modules worden toegevoegd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 geïnstalleerd is. De patch-id is MDVA-41628. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beperkte admin gebruikers kunnen toegang tot de nieuwe middelen krijgen wanneer de nieuwe modules worden toegevoegd.

<u> Stappen om </u> te reproduceren:

1. Creeer een nieuwe admin gebruikersrol met beperkte middelen.
1. Maak een nieuwe beheerder onder de rol die u in stap 1 hebt gemaakt.
1. Installeer en laat de douanemodule toe die tot een nieuwe reeks menupunten samen met ACL middelen leidt.
1. Meld u aan met de nieuwe beheerder.

<u> Verwachte resultaten </u>:

De beheerder met beperkte toegang heeft geen toegang tot de zojuist gemaakte menu-items.

<u> Ware resultaten </u>:

De beperkte admin gebruiker kan tot de nieuwe menupunten toegang hebben, alhoewel de nieuwe middelen niet aan de gebruikersrol worden toegewezen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
