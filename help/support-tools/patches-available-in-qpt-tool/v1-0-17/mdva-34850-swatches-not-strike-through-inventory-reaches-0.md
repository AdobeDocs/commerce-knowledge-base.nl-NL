---
title: '"MDVA-34850: stalen zonder doorslagvoorraad bereiken "0"'
description: De patch MDVA-34850 verhelpt het probleem waarbij de stalen niet worden doorgenomen wanneer de voorraad "0" bereikt en niet zichtbaar zijn in de koppeling Product Details Page (PDP) naar andere stalen in de voorraad. De **Display Out-of-Stock Products** is ook ingesteld op *Yes* in de beheerconfiguratie. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 90f5cef4-137a-426d-a447-2d1aca23e6c1
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# MDVA-34850: stalen zonder doorslagvoorraad bereiken &quot;0&quot;

De patch MDVA-34850 verhelpt het probleem waarbij de stalen niet worden doorgenomen wanneer de voorraad &quot;0&quot; bereikt en niet zichtbaar zijn in de koppeling Product Details Page (PDP) naar andere stalen in de voorraad. De **Producten uit de voorraad weergeven** is ook ingesteld op *Ja* in de beheerdersconfiguratie. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.1 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De opties voor producten uit de voorraad worden niet weergegeven op de PDP-pagina wanneer de standaardvoorraad niet wordt gebruikt en **Producten uit de voorraad weergeven** configuratie is ingeschakeld.

<u>Vereisten</u>:

* Meerbroninventarisatie (MSI) installeren.
* Weergave van producten uit de voorraad inschakelen in [Voorraadvoorraadopties](https://docs.magento.com/user-guide/configuration/catalog/inventory.html).

<u>Stappen om te reproduceren</u>:

1. Nieuwe voorraad maken \[Nieuwe voorraad\], alle websites toewijzen aan deze voorraad en de bovenstaande bron. De standaardvoorraad mag nu niet worden gebruikt.
1. Een [configureerbaar product](https://docs.magento.com/user-guide/catalog/product-create-configurable.html) drie formaatopties toevoegen \[S,M,L\].
1. Open elke optie en voeg hoeveelheden toe door alleen de aangepaste bron \[new\_source\] toe te wijzen. Stel \[Bronstatus\] ook in op \[In voorraad\].
1. Wijzig de index en controleer het configureerbare product vanaf de voorzijde. Alle drie de opties moeten zichtbaar zijn.
1. Open een eenvoudig product dat aan \[size:S\] is toegewezen vanaf de achtergrond en stel \[Source Status\] in op \[Out of Stock\] en werk de hoeveelheid bij op 0. Wijzig de index en controleer het configureerbare product vanaf de voorzijde.

<u>Verwachte resultaten</u>:

Aangezien de optie Producten uit voorraad weergeven is ingeschakeld, moeten alle drie opties worden weergegeven. De optie Out-of-Stock \[S\] moet worden uitgeschakeld en uitgesneden. Het moet 2 x van 1 optieproduct tonen met prijs = 12x2 in orde details op het front en het achtereind.

<u>Werkelijke resultaten</u>:

De optie Uit-van-voorraad is verborgen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
