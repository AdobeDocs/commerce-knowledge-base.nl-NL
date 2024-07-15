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

De patch MDVA-34850 verhelpt het probleem waarbij de stalen niet worden doorgenomen wanneer de voorraad &quot;0&quot; bereikt en niet zichtbaar zijn in de koppeling Product Details Page (PDP) naar andere stalen in de voorraad. De **Vertoning uit-van-voorraad Producten** wordt ook geplaatst aan *ja* in adminconfiguratie. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.1 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De opties van het Product uit-van-voorraad tonen niet op de Pdp- pagina wanneer de standaardinventarisvoorraad niet in gebruik is en **configuratie van de Producten van de Vertoning uit-van-voorraad** wordt toegelaten.

<u> Eerste vereisten </u>:

* Multi-Source Inventory (MSI) installeren.
* Laat de Producten van de Vertoning uit-van-voorraad in [ Opties van de Voorraad van de Voorraad ](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) toe.

<u> Stappen om </u> te reproduceren:

1. Nieuwe voorraad maken \[Nieuwe voorraad\], alle websites toewijzen aan deze voorraad en de bovenstaande bron. De standaardvoorraad mag nu niet worden gebruikt.
1. Creeer a [ configureerbaar product ](https://docs.magento.com/user-guide/catalog/product-create-configurable.html) toevoegend drie grootteopties \ [S, M, L \].
1. Open elke optie en voeg hoeveelheden toe door alleen de aangepaste bron \[new\_source\] toe te wijzen. Stel \[Source Status\] ook in op \[In voorraad\].
1. Wijzig de index en controleer het configureerbare product vanaf de voorzijde. Alle drie de opties moeten zichtbaar zijn.
1. Open een eenvoudig product dat aan \[size:S\] is toegewezen vanaf de achtergrond en stel de \[Source Status\] in op \[Out of Stock\] en werk de hoeveelheid bij op 0. Wijzig de index en controleer het configureerbare product vanaf de voorzijde.

<u> Verwachte resultaten </u>:

Aangezien de optie Producten uit voorraad weergeven is ingeschakeld, moeten alle drie opties worden weergegeven. De optie Out-of-Stock \[S\] moet worden uitgeschakeld en uitgesneden. Het moet 2 x van 1 optieproduct tonen met prijs = 12x2 in orde details op het front en het achtereind.

<u> Ware resultaten </u>:

De optie Uit-van-voorraad is verborgen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
