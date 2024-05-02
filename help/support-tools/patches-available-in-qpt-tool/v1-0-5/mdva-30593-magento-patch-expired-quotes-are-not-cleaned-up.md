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

Met de MDVA-30593-patch wordt het probleem opgelost waarbij aanhalingstekens die volgens de **Offerteleven** niet worden opgeschoond. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.3.4.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.3.0-2.3.3.x

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aanhalingstekens, die volgens de **Offerteleven** niet worden opgeschoond.

<u>Stappen om te reproduceren:</u>

1. Ga in Commerce Admin naar **Winkels** > **Configuratie** > **Verkoop** > **Afhandeling** > **Winkelwagentje**.
1. Set **Aanbiedingslevensduur (dagen)** = *1*
1. Configuratie opslaan en cache wissen.
1. Meld u aan als klant.
1. Voeg een product toe aan de kar.
1. Ga na een dag terug naar de wagen.

<u>Verwacht resultaat:</u>

De prijsopgave wordt gewist en het product wordt uit het winkelwagentje verwijderd, omdat de oude prijs niet langer geldig is.

<u>Werkelijk resultaat:</u>

Het product bevindt zich nog in de kar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
