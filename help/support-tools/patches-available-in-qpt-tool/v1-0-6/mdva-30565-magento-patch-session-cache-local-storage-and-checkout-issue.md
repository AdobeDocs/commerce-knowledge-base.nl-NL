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

De MDVA-30565-patch lost het probleem op met de lokale opslag en het uitchecken van sessiecache. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce op cloudinfrastructuur 2.3.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De punten van het winkelwagentje kunnen nog op de kartpagina worden gezien wanneer een klantenzittingstijden uit. Dit veroorzaakt een fout van de geschatte verzendmethode waar geen verzendmethodes voor gastafhandeling beschikbaar zijn.

<u>Stappen om te reproduceren</u>:

1. Schakel een hardnekkig winkelwagentje in de Commerce Admin in. (**Persistentie inschakelen** = &quot;*Ja*&quot;)
1. Meld u aan als klant op de voorzijde. Hierdoor worden de `persistent_shopping_cart` cookie en start een permanente sessie.
1. Voeg een product toe aan de kar.
1. Wacht tot de frontend zitting uit wordt getimed, of schrap `PHPSESSID` cookie.
1. Nu bent u een gastgebruiker, maar als u naar de kar gaat, kunt u nog het product zien dat als het programma geopende klant werd toegevoegd.
1. Verwijder het product uit de kar en nu is de kar leeg. U ziet dat Adobe Commerce de opdracht `persistent_shopping_cart` cookie in deze gebeurtenis.
1. Voeg een nieuw product toe aan het winkelwagentje en ga naar de winkelwagentje.
1. In de browserconsole wordt nu getoond `V1/guest-carts/4/estimate-shipping-methods` Het verzoek keert nu een 404 reactie met bericht terug `{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}`

<u>Verwachte resultaten</u>:

De aanvraag voor de geschatte verzendmethode retourneert de juiste resultaten.

<u>Werkelijke resultaten</u>:

De aanvraag voor de geschatte verzendmethode mislukt met een fout zoals &quot;*Er zijn momenteel geen aanhalingstekens beschikbaar voor deze bestelling.*&quot;

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
