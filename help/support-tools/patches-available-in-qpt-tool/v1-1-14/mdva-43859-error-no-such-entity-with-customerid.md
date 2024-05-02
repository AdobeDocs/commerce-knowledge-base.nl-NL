---
title: '''MDVA-43859: Fout "Geen dergelijke entiteit met customerId =" geregistreerd wanneer verwijderde klant zich aanmeldt"'
description: De patch MDVA-43859 lost het probleem op waar fout *No zulk een entiteit met customerId =* wordt geregistreerd wanneer een geschrapte klant probeert om binnen te registreren. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43859. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 62c4b6ee-88a0-40b8-9eb2-37b6cefa0b83
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-43859: Fout &quot;Geen dergelijke entiteit met customerId =&quot;het programma wordt geopend wanneer de geschrapte klant het programma opent

De MDVA-43859-patch verhelpt het probleem waarbij de fout *Geen dergelijke entiteit met customerId =* wordt geregistreerd wanneer een verwijderde klant probeert zich aan te melden. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43859. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De fout *Geen dergelijke entiteit met customerId =* wordt geregistreerd wanneer een verwijderde klant probeert zich aan te melden.

<u>Stappen om te reproduceren</u>:

1. Maak een klantenaccount aan de voorzijde.
1. Meld u af en meld u aan bij de klantenaccount die u in stap 1 hebt gemaakt.
1. Laad de backend in een andere browser en ga naar het klantenraster.
1. Verwijder de klant die u in stap 1 hebt gemaakt.
1. Ga terug naar de eerste browser en probeer u af te melden.

<u>Verwachte resultaten</u>:

De klant wordt zonder fout omgeleid naar de aanmeldingspagina.

<u>Werkelijke resultaten</u>:

De klant krijgt de volgende fout: *Geen dergelijke entiteit met customerId =*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
