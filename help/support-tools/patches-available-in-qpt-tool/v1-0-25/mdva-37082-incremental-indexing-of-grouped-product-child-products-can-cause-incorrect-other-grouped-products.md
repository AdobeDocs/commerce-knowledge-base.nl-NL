---
title: "MDVA-37082: Onjuiste gedeeltelijke index van de voorraadstatus voor gegroepeerde producten"
description: De patch voor het Magento MDVA-37082 verhelpt het probleem wanneer de gedeeltelijke index van de voorraadstatus voor gegroepeerde producten onjuist is voor aangepaste voorraden. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 is geïnstalleerd. De patch-id is MDVA-37082. De kwestie zal volgens de planning worden opgelost in Magento 2.4.4.
exl-id: 1c0abc99-bd24-4848-87a3-227a63655cb7
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-37082: Onjuiste gedeeltelijke index van de voorraadstatus voor gegroepeerde producten

De patch voor het Magento MDVA-37082 verhelpt het probleem wanneer de gedeeltelijke index van de voorraadstatus voor gegroepeerde producten onjuist is voor aangepaste voorraden. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 is geïnstalleerd. De patch-id is MDVA-37082. De kwestie zal volgens de planning worden opgelost in Magento 2.4.4.


## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met Adobe Commerce-versies:**
Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0-2.4.2-p1
>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het incrementele indexeren van gegroepeerde onderliggende producten kan ertoe leiden dat onjuiste andere gegroepeerde producten onjuist worden geïndexeerd wanneer onderliggende producten worden gedeeld.

<u>Stappen om te reproduceren</u>:

* Maak een nieuwe voorraad en bron voor de hoofdwebsite.
* Maak drie eenvoudige producten met een hoeveelheid van 10,15 en 0.
* Maak twee gegroepeerde producten en stel het eerste eenvoudige product samen met een hoeveelheid van 10 tot en met een andere 2 eenvoudige producten.
* Bevestig dat beide gegroepeerde producten vanaf de voorzijde in voorraad toegankelijk zijn.
* Wijs het eenvoudige product met hoeveelheid 0 toe aan de producten van de eerste gegroepeerde verkoopactiviteiten.
* Reinig de cache van volledige pagina en controleer het tweede gegroepeerde product vanaf de voorkant.
* Voer een volledige re-index uit.
* Controleer het tweede gegroepeerde product vanaf de voorkant.
* Sla het eerste gegroepeerde product op.
* Cache van volledige pagina opschonen en het tweede gegroepeerde product vanaf de voorzijde controleren.

<u>Verwachte resultaten</u>:

Gegroepeerd product is niet uit voorraad nadat een ander Gegroepeerd product met Up-sell is opgeslagen. Het probleem wordt opgelost na een volledige herindex.

<u>Werkelijke resultaten</u>:

Het tweede gegroepeerde product heeft geen voorraad wanneer u het eerste gegroepeerde product opslaat.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen naar de documentatie voor ontwikkelaars, afhankelijk van uw Adobe Commerce-implementatiemethode:

* Adobe Commerce ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor het probleem van het Magento met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
