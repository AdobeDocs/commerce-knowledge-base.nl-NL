---
title: "MDVA-41061: Voorraadstatus kan opnieuw worden verkocht wanneer het product wordt opgeslagen bij Admin"
description: De MDVA-41061-patch verhelpt het probleem waarbij de status van de voorraad wordt hersteld naar de verkoopbaarheid wanneer het product wordt opgeslagen bij de Admin. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41061. De nieuwste patchversie is beschikbaar in QPT 1.1.15 met MDVA-41061-V3 patch-id. De kwestie is opgelost in Adobe Commerce 2.4.4.
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061: Voorraadstatus kan opnieuw worden verkocht wanneer het product wordt opgeslagen bij Admin

De MDVA-41061-patch verhelpt het probleem waarbij de status van de voorraad wordt hersteld naar de verkoopbaarheid wanneer het product wordt opgeslagen bij de Admin. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41061. De nieuwste patchversie is beschikbaar in QPT 1.1.15 met MDVA-41061-V3 patch-id. De kwestie is opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van de voorraad kan opnieuw worden verkocht wanneer het product bij de beheerder wordt opgeslagen.

<u>Vereisten</u>:

De inventarismodules worden geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Maak een eenvoudig product met Aantal = 1.
1. Plaats een bestelling met het product dat u in stap 1 hebt gemaakt.
1. Uitsnede uitvoeren - zorg ervoor `inventory.reservations.updateSalabilityStatus` de wachtrij wordt uitgevoerd en de status van de productvoorraad is in het dialoogvenster `cataloginventory_stock_status` tabel.
1. Controleer het product op de voorzijde. Het moet als **Uit voorraad**.
1. Sla het product zonder wijzigingen op in de Admin.

<u>Verwachte resultaten</u>:

* De voorraadstatus moet niet worden bijgewerkt.
* Het product moet **Uit voorraad** op de voorzijde.

<u>Werkelijke resultaten</u>:

* Eenvoudig product is gemarkeerd als **In voorraad** op de voorzijde.
* Gebruikers krijgen *De gevraagde hoeveelheid is niet beschikbaar* bericht wanneer u probeert het aan de winkelwagen toe te voegen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
