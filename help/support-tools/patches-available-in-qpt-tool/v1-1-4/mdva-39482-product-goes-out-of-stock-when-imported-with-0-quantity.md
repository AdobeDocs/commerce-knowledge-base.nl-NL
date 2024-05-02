---
title: "MDVA-39482: Het product is uit voorraad wanneer het wordt ingevoerd met de hoeveelheid '0' en de hoeveelheid backorders ingeschakeld."
description: In de MDVA-39482 is bepaald dat het product uit de voorraad komt als het met "0"-hoeveelheid wordt ingevoerd als MSI en backorders zijn ingeschakeld en de drempel voor de uit-van-voorraad wordt ingesteld op een minwaarde. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 is geïnstalleerd. De patch-id is MDVA-39482. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 2caf461c-993d-48b3-bc47-3fa1d014deaf
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39482: Het product is uit voorraad als het wordt geïmporteerd met de hoeveelheid &#39;0&#39; en de optie &#39;backorders&#39; ingeschakeld

In de MDVA-39482 is bepaald dat het product uit de voorraad komt als het met &quot;0&quot;-hoeveelheid wordt ingevoerd als MSI en backorders zijn ingeschakeld en de drempel voor de uit-van-voorraad wordt ingesteld op een minwaarde. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 is geïnstalleerd. De patch-id is MDVA-39482. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het product gaat uit voorraad als het wordt ingevoerd met &quot;0&quot; hoeveelheid wanneer MSI en backorders worden toegelaten en de Drempel van de Voorraad aan een minwaarde wordt geplaatst.

<u>Vereisten</u>:

1. MSI- en voorbeeldgegevens moeten worden geïnstalleerd.
1. Ga naar **Winkels** > **Configuraties** > **Catalogus** > **Inventaris**:
   * Achterorden instellen op &quot;Aantal onder 0 toestaan&quot;
   * Drempel voor verstreken bestanden instellen op &quot;-10&quot;

<u>Stappen om te reproduceren</u>:

1. Zorg ervoor dat de SKU **In voorraad** en heeft hoeveelheid **24 MB01**.
1. Importeer de CSV van de voorraden. Zorg ervoor dat u &quot;Stock Sources&quot; selecteert in Type entiteit:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Controleer de voorraadstatus van het product nadat de voorraden zijn ingevoerd.

<u>Verwachte resultaten</u>:

24 MB01 is **In voorraad** in Storefront.

<u>Werkelijke resultaten</u>:

24 MB01 is **Buiten de voorraad** in Storefront.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
