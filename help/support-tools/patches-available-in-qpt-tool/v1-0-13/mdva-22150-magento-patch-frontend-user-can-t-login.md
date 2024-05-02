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

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.3.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.3.2

**Compatibel met Adobe Commerce-versies:** Adobe Commerce over cloudinfrastructuur en Adobe Commerce 2.3.1 - 2.3.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren:</u>

1. Meld u aan bij de beheerder en maak een configureerbaar product.
1. Ga naar **Winkelregels** en maak een couponcode met korting.
1. Maak een klantenaccount op de voorgrond.
1. Voeg het product toe aan de winkelwagentje, volg het afrekenproces en voer de coupon in.
1. Nadat u de coupon hebt ingevoerd, verzendt u de bestelling niet, maar u kunt de bestelling afbreken en zich afmelden.
1. Ga terug naar Admin en maak het volledige configureerbare product onbruikbaar.

<u>Verwachte resultaten:</u>

Het product wordt niet weergegeven in het winkelwagentje of weergegeven met het juiste foutbericht dat het product is uitgeschakeld, zoals u had verwacht.

<u>Werkelijke resultaten:</u>

* Wanneer het proberen om terug in frontend te registreren, zult u in een oneindige lijn worden geplakt (die uiteindelijk een uitzondering na een lange hoeveelheid tijd zal tonen).
* De mogelijkheid om de winkelwagentjes van de klant in de Admin te beheren, werkt niet meer.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
