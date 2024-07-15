---
title: 'MDVA-31021: langzaam importeren en exporteren als er veel productopties zijn'
description: De MDVA-31021-patch lost het probleem op wanneer het importeren/exporteren langer duurt dan verwacht bij een groot aantal productopties. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd.
exl-id: d294b30d-b734-4bd6-bf1a-c116b789a63c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-31021: langzaam importeren en exporteren als er veel productopties zijn

De MDVA-31021-patch lost het probleem op wanneer het importeren/exporteren langer duurt dan verwacht bij een groot aantal productopties. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 geïnstalleerd is.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.3.1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als de tabel `catalog_product_option` 100.000 records of meer bevat, duurt de validatie van het functiebestand Importeren/exporteren langer dan verwacht. Voordat u gaat importeren/exporteren, laadt Adobe Commerce voor het controleren van de validatie van opties productopties voor alle bestaande producten.

<u> Eerste vereisten </u>:

Adobe Commerce-winkel met 5000 producten met aangepaste opties. Elk product moet ten minste vier aangepaste opties hebben waaruit twee of meer opties kunnen worden gekozen, zodat de tabel 100.000 records bevat. `catalog_product_option`

<u> Stappen om </u> te reproduceren:

1. Voor een **Invoer** voorbeeld: creeer een CSV invoerdossier met één van SKUs van Commerce Admin.
1. Voeg vier aangepaste opties toe aan het CSV-importbestand.
1. Probeer het CSV-bestand te importeren vanuit Commerce Admin.

<u> Verwachte resultaten </u>:

De functie Importeren of Exporteren wordt naar behoren uitgevoerd. Validatie duurt minder dan 10 seconden om te voltooien met één product.

<u> Ware resultaten </u>:

De functie Importeren of Exporteren duurt langer dan u had verwacht. Validatie duurt meer dan 10 seconden om te voltooien met slechts één product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
