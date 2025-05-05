---
title: 'MDVA-40961: Er kan geen extra item aan het winkelwagentje worden toegevoegd als de minimumhoeveelheid item al in het winkelwagentje staat'
description: De MDVA-40961-patch verhelpt het probleem dat een extra item niet aan het winkelwagentje kan worden toegevoegd als de minimumhoeveelheid van het item al in het winkelwagentje staat. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-40961. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: fc90c2b6-f631-49ff-81b0-e41918dd79a7
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-40961: Er kan geen extra item aan het winkelwagentje worden toegevoegd als de minimumhoeveelheid item al in het winkelwagentje staat

De MDVA-40961-patch verhelpt het probleem dat een extra item niet aan het winkelwagentje kan worden toegevoegd als de minimumhoeveelheid van het item al in het winkelwagentje staat. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 geïnstalleerd is. De patch-id is MDVA-40961. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een extra item kan niet aan het winkelwagentje worden toegevoegd als de minimumhoeveelheid van het artikel al in het winkelwagentje staat.

<u> Stappen om </u> te reproduceren:

1. Plaats een eenvoudig product om meer dan één **Minimale Aantal te hebben dat in het Winkelen van Kaart** wordt toegestaan (bijvoorbeeld, twee).
1. Open het product op de Storefront en voeg er twee toe aan het winkelwagentje.
1. Blijf op de productpagina en voeg nog een product aan de winkelwagentje toe.

<u> Verwachte resultaten </u>:

Het derde product kan aan het karretje worden toegevoegd omdat het al de minimumhoeveelheid bevat.

<u> Ware resultaten </u>:

U krijgt het volgende foutenbericht: *het minste u kunt kopen is 2*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
