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

De patch MDVA-30107 lost het probleem op waar de opslagschakelaar niet zoals verwacht werkt als verschillende basis-URL&#39;s voor opslagmeningen worden gebruikt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.3.0 - 2.3.5.x
* Adobe Commerce op cloudinfrastructuur 2.3.0 - 2.3.5.x

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een gebruiker tussen opslagplaatsen gebruikend de opslagschakelaar schakelt, ontbreekt het verzoek als de doelopslag een verschillende basis URL heeft.

<u>Stappen om te reproduceren</u>:

1. Maak twee of meer winkels met verschillende basis-URL&#39;s.
1. Ga naar een categoriepagina op een winkel van een van deze winkels.
1. Probeer over te schakelen naar de andere winkel met behulp van de winkelswitch.

<u>Verwachte resultaten</u>:

U wordt omgeleid naar een vergelijkbare pagina van de andere winkel.

<u>Werkelijke resultaten</u>:

U wordt omgeleid naar de homepage van dezelfde winkel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
