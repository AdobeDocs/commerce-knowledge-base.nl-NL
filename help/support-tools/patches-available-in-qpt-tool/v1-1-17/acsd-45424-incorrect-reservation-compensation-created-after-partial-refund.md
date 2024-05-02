---
title: "ACSD-45424: Onjuiste reserveringscompensatie na gedeeltelijke terugbetaling"
description: De ACSD-45424-patch verhelpt het probleem dat na een gedeeltelijke terugbetaling een onjuiste reserveringscompensatie wordt gecreëerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-45424. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 0676cfda-a28e-4a66-a75b-8a3fc5e22566
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# ACSD-45424: Onjuiste reserveringscompensatie na gedeeltelijke terugbetaling

De ACSD-45424-patch verhelpt het probleem dat na een gedeeltelijke terugbetaling een onjuiste reserveringscompensatie wordt gecreëerd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-45424. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Na een gedeeltelijke terugbetaling wordt een onjuiste reserveringscompensatie tot stand gebracht.

<u>Stappen om te reproduceren</u>:

1. Verzendmethode voor in-store levering inschakelen.
1. Maak drie inventarisbronnen en zorg ervoor dat de ophaallocatie actief is in elke bron (bron1, bron2, bron3).
1. Maak een nieuw bestand en wijs de drie bronnen toe aan het nieuwe bestand.
   * Dit bestand moet worden toegewezen aan de hoofdwebsite.
1. Creeer een eenvoudig product, P3, en wijs alle bronnen aan het toe.
1. Voeg de volgende hoeveelheden voor de bronnen van het eenvoudige product toe en laat backorders toe:
   * Standaardbron - 100
   * bron1 - 0
   * bron2 - 10
   * bron3 - 0
1. Voeg het eenvoudige product vanaf de voorkant toe aan de winkelwagentje en ga door naar het verzendformulier.
1. Selecteer &quot;source1&quot; als verzendlocatie.
1. Voltooi de orde en voer de volgende vraag in het gegevensbestand uit:

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   U krijgt de geplaatste opdracht record in het dialoogvenster `inventory_reservation` tabel. De hoeveelheid is 10, wat juist is.
1. Factureer deze volgorde vanaf de achterkant.
1. Maak nu een creditmemo voor slechts één product. NIET selecteren *Terug naar voorraad* selectievakje.
1. Voer de zelfde vraag van Stap 8 uit.

<u>Verwachte resultaten</u>:

Als u de *Terug naar voorraad* tijdens het aanmaken van de kredietnota `inventory_reservation` de tabel bevat geen record die overeenkomt met de creditnota.

<u>Werkelijke resultaten</u>:

Ook al hebt u de *Terug naar voorraad* tijdens het aanmaken van de kredietmemo wordt een record toegevoegd aan `inventory_reservation` tabel met `creditmemo_created` gebeurtenistype. Ook de in de `inventory_reservation` de tabel heeft een hoeveelheid van 10, ook al hebt u slechts voor één hoeveelheid een creditmemo gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
