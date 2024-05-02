---
title: 'MDVA-41164: Kan bedrijf met aangepaste klantkenmerken niet opslaan of bewerken'
description: Met de MDVA-41164-patch wordt het probleem opgelost waarbij de beheerder een bedrijf met aangepaste klantkenmerken van bestanden of afbeeldingen van een willekeurig type niet kan opslaan of bewerken. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41164. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 24338895-68b4-404c-bedd-46cfc7e983a0
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-41164: Kan bedrijf met de attributen van de douaneklanten niet opslaan of uitgeven

Met de MDVA-41164-patch wordt het probleem opgelost waarbij de beheerder een bedrijf met aangepaste klantkenmerken van bestanden of afbeeldingen van een willekeurig type niet kan opslaan of bewerken. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41164. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruiker kan een bedrijf met aangepaste klantkenmerken van bestanden of afbeeldingen van welk type dan ook niet opslaan of bewerken.

<u>Vereisten</u>:

B2B-module is geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Bedrijf inschakelen in **Winkels** > **Config** > **B2B-functies**.
1. Een klantkenmerk maken in **Winkels** > **Attributen** > **Klanten** > **Nieuw kenmerk toevoegen**:
   * Invoertype: Bestand (bijlage)
   * Tonen in winkelcentrum: Ja
   * Sorteervolgorde: alle
   * Forms voor gebruik in: alles selecteren
1. Een nieuw bedrijf maken in **Klanten** > **Bedrijven** > **Nieuw bedrijf toevoegen** en uploadt u een bestand voor het nieuwe hierboven gemaakte kenmerk.

<u>Verwachte resultaten</u>:

De gebruiker kan de creatie van het bedrijf voltooien en de gehechtheid wordt geupload zonder enige fout.

<u>Werkelijke resultaten</u>:

* Er verschijnt een foutbericht: *Er is iets misgegaan tijdens het opslaan van het bestand.*
* Het logboek van de uitzondering bevat een verslag als het volgende:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
