---
title: 'MDVA-33970 patch: currency sign in credit memo'
description: De patch MDVA-33970 lost het probleem op waarbij een Dollar ($)-teken werd weergegeven in plaats van de gelokaliseerde valuta in een creditmemo. Dit gebeurt wanneer een bereik **Website** wordt gebruikt voor een kenmerk **Price**.
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# MDVA-33970 patch: currency sign in credit memo

De patch MDVA-33970 lost het probleem op waarbij een Dollar ($)-teken werd weergegeven in plaats van de gelokaliseerde valuta in een creditmemo. Dit gebeurt wanneer een **Website** bereik wordt gebruikt voor een **Prijs** kenmerk.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Voorwaarden</u>:

In dit voorbeeld worden de volgende instellingen gebruikt:

* 2 websites bestaan - elk heeft een **Winkel** en **Winkelweergave**.
* De **Standaardconfiguratie** heeft de Singaporese dollar als **Valuta** (**Stores > Configuration > General > Currency Setup**):
   * **Basisvaluta** = *Singaporese dollar*
   * **Standaardweergavemunt** = *Singaporese dollar*
   * **Toegestane valuta&#39;s** = *Singaporese dollar*
* **Website 1** heeft een **Standaardconfiguratie**.
* **Website 2** heeft de Maleisische ringgit als **Valuta**:
   * **Basisvaluta** = *Maleisische ringgit*
   * **Standaardweergavemunt** = *Maleisische ringgit*
   * **Toegestane valuta&#39;s** = *Maleisische ringgit*
* Ga naar **Winkels > Valutasymbolen** en Set:
   * **MYR (Maleisische ringgit)** = *RM*
   * **SGD (Singaporese dollar)** = *SGD* (**Standaard gebruiken** = *Ingeschakeld*)
* Sommige **Product** bestaat.

<u>Stappen om te reproduceren</u>:

1. Maak een **Volgorde** van de **Website 2** (U kunt de standaardinstelling instellen om extra instellingen te voorkomen).
1. Aanmelden bij **Beheerder**.
1. Open de nieuwe volgorde.
1. Controleer of de **Valutasymbool** = *RM*.
1. Een **Factuur**.
1. Controleer of de **Valutasymbool** = *RM* in de factuur.
1. Een **Kredietfaciliteit**.
1. Controleer of de **Valutasymbool**  ** ** = *RM* in de **Kredietfaciliteit**.
1. Open de **Creditnota&#39;s** tab in **Volgorde**.
1. Controleer de **Valutasymbool** in het raster.
1. Openen **Verkoop > Creditnota&#39;s**.
1. Controleer de **Valutasymbool** in het raster.

<u>Verwachte resultaten</u>:

Het correcte gelokaliseerde valutasymbool wordt gebruikt, zoals verwacht.

<u>Werkelijke resultaten</u>:

Het Dollar-teken ($) wordt gebruikt, ook al is dit niet ingesteld in de beheerinstellingen.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
