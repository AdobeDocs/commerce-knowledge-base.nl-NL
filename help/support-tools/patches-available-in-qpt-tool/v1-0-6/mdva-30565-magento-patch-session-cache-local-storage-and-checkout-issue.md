---
title: 'MDVA-30565: probleem met lokale opslag en uitchecken van sessiecache'
description: De MDVA-30565-patch lost het probleem op met de lokale opslag en het uitchecken van sessiecache. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd.
exl-id: f0693f0c-fc6b-44af-a6a0-ebfa973bca65
feature: Cache, Checkout, Orders, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-30565: probleem met lokale opslag en uitchecken van sessiecache

De MDVA-30565-patch lost het probleem op met de lokale opslag en het uitchecken van sessiecache. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 geïnstalleerd is.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce op cloudinfrastructuur 2.3.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De punten van het winkelwagentje kunnen nog op de kartpagina worden gezien wanneer een klantenzittingstijden uit. Dit veroorzaakt een fout van de geschatte verzendmethode waar geen verzendmethodes voor gastafhandeling beschikbaar zijn.

<u> Stappen om </u> te reproduceren:

1. Schakel een hardnekkig winkelwagentje in de Commerce Admin in. (**laat persistentie** toe = &quot;*ja*&quot;)
1. Meld u aan als klant op de voorzijde. Hierdoor wordt het `persistent_shopping_cart` -cookie gemaakt en wordt een permanente sessie gestart.
1. Voeg een product toe aan de kar.
1. Wacht tot er een time-out is opgetreden voor de frontend-sessie of verwijder het `PHPSESSID` -cookie.
1. Nu bent u een gastgebruiker, maar als u naar de kar gaat, kunt u nog het product zien dat als het programma geopende klant werd toegevoegd.
1. Verwijder het product uit de kar en nu is de kar leeg. In deze gebeurtenis verwijdert Adobe Commerce het `persistent_shopping_cart` -cookie.
1. Voeg een nieuw product toe aan het winkelwagentje en ga naar de winkelwagentje.
1. In de browserconsole wordt nu getoond dat de `V1/guest-carts/4/estimate-shipping-methods` -aanvraag nu een reactie van 404 weergeeft met bericht `{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}`

<u> Verwachte resultaten </u>:

De aanvraag voor de geschatte verzendmethode retourneert de juiste resultaten.

<u> Ware resultaten </u>:

De schatting verschepende methodeverzoek ontbreekt met een fout als, &quot;*Sorry, zijn geen citaten beschikbaar voor deze orde op dit ogenblik.*&quot;

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
