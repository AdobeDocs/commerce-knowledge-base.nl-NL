---
title: 'MDVA-30107: Winkelschakelaar werkt niet zoals verwacht'
description: De patch MDVA-30107 lost het probleem op waar de opslagschakelaar niet zoals verwacht werkt als verschillende basis-URL's voor opslagmeningen worden gebruikt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd.
exl-id: feaef9ed-615f-4a0a-a7c5-1833f993d27f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-30107: Winkelschakelaar werkt niet zoals verwacht

De patch MDVA-30107 lost het probleem op waar de opslagschakelaar niet zoals verwacht werkt als verschillende basis-URL&#39;s voor opslagmeningen worden gebruikt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 geïnstalleerd is.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.3.0 - 2.3.5.x
* Adobe Commerce op cloudinfrastructuur 2.3.0 - 2.3.5.x

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een gebruiker tussen opslagplaatsen gebruikend de opslagschakelaar schakelt, ontbreekt het verzoek als de doelopslag een verschillende basis URL heeft.

<u> Stappen om </u> te reproduceren:

1. Maak twee of meer winkels met verschillende basis-URL&#39;s.
1. Ga naar een categoriepagina op een winkel van een van deze winkels.
1. Probeer over te schakelen naar de andere winkel met behulp van de winkelswitch.

<u> Verwachte resultaten </u>:

U wordt omgeleid naar een vergelijkbare pagina van de andere winkel.

<u> Ware resultaten </u>:

U wordt omgeleid naar de homepage van dezelfde winkel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
