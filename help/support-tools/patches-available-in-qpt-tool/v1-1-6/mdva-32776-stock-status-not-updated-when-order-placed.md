---
title: "MDVA-32776: voorraadstatus niet bijgewerkt met orderplaatsing"
description: De MDVA-32776-patch verhelpt het probleem waarbij de voorraadstatus niet wordt bijgewerkt wanneer een bestelling wordt geplaatst, maar niet wordt verzonden. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 is geïnstalleerd. De patch-id is MDVA-32776. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776: voorraadstatus niet bijgewerkt met orderplaatsing

De MDVA-32776-patch verhelpt het probleem waarbij de voorraadstatus niet wordt bijgewerkt wanneer een bestelling wordt geplaatst, maar niet wordt verzonden. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 is geïnstalleerd. De patch-id is MDVA-32776. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.0

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De voorraadstatus wordt niet bijgewerkt wanneer een bestelling wordt geplaatst maar niet verzonden.

<u>Vereisten</u>:

1. De voorraadmodule is geïnstalleerd.
1. Weergave van producten uit de wachtrij is ingesteld op *Ja*.

   Ga naar **Winkels** > **Configuratie** > **Catalogus** > **Inventaris** > **Producten uit de voorraad weergeven** = *Ja*.

<u>Stappen om te reproduceren</u>:

1. Maak twee eenvoudige producten met qty = 11 en 22.
1. Maak een gegroepeerd product met de eenvoudige producten die in stap 1 worden gemaakt.
1. Voeg gegroepeerde producten aan de kar toe door één van de producthoeveelheid aan 11 te plaatsen en het andere eenvoudige product uit voorraad te maken.
1. Voltooi het afrekenen en plaats de bestelling.

<u>Verwachte resultaten</u>:

Gegroepeerde weergave van producten `out-of-stock` etiketten wanneer de bijbehorende eenvoudige producten uit voorraad verdwijnen.

<u>Werkelijke resultaten</u>:

1. Het eenvoudige product met qty = 11 is uit voorraad.
1. Het gegroepeerde product bevat geen *uit voorraad* bericht voor het product met qty = 11. Als u dit product echter aan het winkelwagentje toevoegt, krijgt u een *uit voorraad* fout.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
