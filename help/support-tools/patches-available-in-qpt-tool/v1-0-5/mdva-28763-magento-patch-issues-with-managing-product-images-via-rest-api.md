---
title: 'MDVA-28763: problemen met het beheer van productafbeeldingen via REST API'
description: Met de MDVA-28763-patch worden meerdere problemen opgelost die te maken hebben met het beheer van de mediagalerie met behulp van REST API. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd. De problemen worden in latere Adobe Commerce-versies opgelost.
exl-id: 736fbfa8-b6a3-413c-a220-fd772d87ed04
feature: REST, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-28763: problemen met het beheer van productafbeeldingen via REST API

Met de MDVA-28763-patch worden meerdere problemen opgelost die te maken hebben met het beheer van de mediagalerie met behulp van REST API. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd. De problemen worden volgens planning opgelost in latere Adobe Commerce-versies (zie de beschrijving van uitgaven in [Problemen](#issues).

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce op locatie 2.3.2 - 2.3.3.x
* Adobe Commerce op cloudinfrastructuur 2.3.2 - 2.3.3.x

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Problemen {#issues}

De patch MDVA-28763 bevat oplossingen voor de volgende problemen die met de mediagalerie samenhangen:

* Als u REST API gebruikt om YouTube-video&#39;s bij te werken (`PUT rest/V1/products/ {SKU}`Adobe Commerce geeft een miniatuur voor de video weer, maar de videospeler wordt niet geladen wanneer u op de knop Afspelen klikt. Gepland in Adobe Commerce 2.3.6.
* `PUT /V1/products/:sku/media/:entryId` De vraag leidt tot een nieuwe ingang eerder dan vervangt bestaande. Vast in Adobe Commerce 2.3.5.
* Problemen met het verwijderen van productafbeeldingen wanneer producten worden toegewezen aan meerdere winkelweergaven. Vast in Adobe Commerce 2.3.4.
* Handelaars met meerdere websites kunnen nu REST gebruiken om producten te maken en bij te werken, terwijl de overerving van afbeeldingen en afbeeldingsrollen behouden blijft. Eerder, toen een handelaar REST gebruikte om producten tot stand te brengen en bij te werken, en een product voor opslagmening werd bijgewerkt, werden de standaardbeeldrollen geladen en voor die archiefmening bewaard. Dientengevolge, hielden de store-view beeldrollen die van het standaardwerkingsgebied na de update erven op. Gepland in Adobe Commerce 2.3.6.
* Mediakenmerken (afbeelding, miniatuur, ...) waarden in winkelweergaven die verwijzen naar verwijderde afbeeldingen die niet automatisch worden opgeschoond. Gepland in Adobe Commerce 2.4.2.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
