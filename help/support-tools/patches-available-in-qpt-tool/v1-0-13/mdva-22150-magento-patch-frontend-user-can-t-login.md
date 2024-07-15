---
title: "MDVA-22150 Adobe Commerce patch: frontend user can't log in"
description: De MDVA-22150-patch lost het probleem op wanneer een frontend gebruiker zich niet kan aanmelden na een afgebroken aankoop met behulp van een coupon. Dit gebeurt wanneer een frontend gebruiker een couponcode gebruikt op een product dat is uitgeschakeld voordat de aankoop wordt voltooid. Het resultaat is dat de voorste gebruiker zich niet meer kan aanmelden en een fout van 503 ontvangt. Een ander effect van dit probleem is dat de mogelijkheid om winkelwagentjes van klanten in de Admin te beheren, niet meer werkt.
exl-id: 8aabe7b2-4b8a-4339-914e-7131006907b3
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# MDVA-22150 Adobe Commerce patch: frontend user can not log in

De MDVA-22150-patch lost het probleem op wanneer een frontend gebruiker zich niet kan aanmelden na een afgebroken aankoop met behulp van een coupon. Dit gebeurt wanneer een frontend gebruiker een couponcode gebruikt op een product dat is uitgeschakeld voordat de aankoop wordt voltooid. Het resultaat is dat de voorste gebruiker zich niet meer kan aanmelden en een fout van 503 ontvangt. Een ander effect van dit probleem is dat de mogelijkheid om winkelwagentjes van klanten in de Admin te beheren, niet meer werkt.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce versie 2.3.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.3.2

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur en Adobe Commerce 2.3.1 - 2.3.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om te reproduceren:</u>

1. Meld u aan bij de beheerder en maak een configureerbaar product.
1. Ga naar **Regels van de Kar**, en creeer een couponcode met één of andere korting.
1. Maak een klantenaccount op de voorgrond.
1. Voeg het product toe aan de winkelwagentje, volg het afrekenproces en voer de coupon in.
1. Nadat u de coupon hebt ingevoerd, verzendt u de bestelling niet, maar u kunt de bestelling afbreken en zich afmelden.
1. Ga terug naar Admin en maak het volledige configureerbare product onbruikbaar.

<u> Verwachte resultaten:</u>

Het product wordt niet weergegeven in het winkelwagentje of weergegeven met het juiste foutbericht dat het product is uitgeschakeld, zoals u had verwacht.

<u> Ware resultaten:</u>

* Wanneer het proberen om terug in frontend te registreren, zult u in een oneindige lijn worden geplakt (die uiteindelijk een uitzondering na een lange hoeveelheid tijd zal tonen).
* De mogelijkheid om de winkelwagentjes van de klant in de Admin te beheren, werkt niet meer.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
