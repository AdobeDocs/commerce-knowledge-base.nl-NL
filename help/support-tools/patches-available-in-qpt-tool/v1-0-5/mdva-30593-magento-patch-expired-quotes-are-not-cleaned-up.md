---
title: "MDVA-30593 patch: expired quotes are not schoonmaakup"
description: De patch MDVA-30593 lost het probleem op waarbij prijsopgaven die volgens de instelling **Quote Lifetime** verlopen, niet worden opgeschoond. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.3.4.
exl-id: 5ee91546-a5cb-4282-bdfc-c9bb3438af50
feature: Cache, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# MDVA-30593-patch: verlopen aanhalingstekens worden niet opgeruimd

Het flard MDVA-30593 lost de kwestie op waar de citaten die volgens het **plaatsen van het Leven van het Citaat** verliepen, niet worden schoongemaakt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.3.4.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.3.0-2.3.3.x

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De citaten, die volgens het **plaatsen van het Leven van het Citaat** verliepen, worden niet schoongemaakt.

<u> Stappen om te reproduceren:</u>

1. In Commerce Admin, ga **>** Configuratie **>** Verkoop **>** Controle **>** het Vormen Kart **.**
1. Plaats **het Leven van het Citaat (dagen)** = *1*
1. Configuratie opslaan en cache wissen.
1. Meld u aan als klant.
1. Voeg een product toe aan de kar.
1. Ga na een dag terug naar de wagen.

<u> Verwacht resultaat:</u>

De prijsopgave wordt gewist en het product wordt uit het winkelwagentje verwijderd, omdat de oude prijs niet langer geldig is.

<u> Ware resultaat:</u>

Het product bevindt zich nog in de kar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
