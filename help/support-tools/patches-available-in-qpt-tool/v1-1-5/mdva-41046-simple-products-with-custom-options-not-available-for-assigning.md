---
title: 'MDVA-41046: Eenvoudige producten met aangepaste opties niet beschikbaar voor toewijzing'
description: De patch MDVA-41046 lost het probleem op waar de eenvoudige producten met douaneopties niet beschikbaar voor het toewijzen aan configureerbaar/gegroepeerd product zijn. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41046. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 01229a69-c72a-4189-9be5-1761073b74ee
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-41046: eenvoudige producten met aangepaste opties die niet beschikbaar zijn voor toewijzing

De patch MDVA-41046 lost het probleem op waar de eenvoudige producten met douaneopties niet beschikbaar voor het toewijzen aan configureerbaar/gegroepeerd product zijn. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41046. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Eenvoudige producten met aangepaste opties zijn niet beschikbaar voor toewijzing aan configureerbaar/gegroepeerd product.

<u>Stappen om te reproduceren</u>:

1. Maak een eenvoudig product met aanpasbare opties en stel een waarde in voor het configureerbare kenmerk.
   * Gebruiken *Kleur* als configureerbaar attribuut, en selecteer *Geel* als de kleurwaarde.
1. Sla het eenvoudige product op.
1. Ga nu naar de aanpasbare productpagina maken.
1. Ga door de wizard &quot;Configuratie maken&quot; en zorg ervoor dat u *Geel* als de kenmerkkleur.
1. Als u het configureerbare product niet wilt opslaan, selecteert u de optie &quot;Kies een ander product&quot; in het vervolgkeuzemenu Selecteren.
1. Hiermee wordt een productraster geopend dat met geel kleurkenmerk is gefilterd. Selecteer nu het eenvoudige product dat eerder met aanpasbare opties werd gecreeerd.
1. Sla het configureerbare product op.

<u>Verwachte resultaten</u>:

Het eenvoudige product met aangepaste opties is beschikbaar voor toewijzing (zichtbaar in het raster) in stap 6.

<u>Werkelijke resultaten</u>:

De sectie Configuratie is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
