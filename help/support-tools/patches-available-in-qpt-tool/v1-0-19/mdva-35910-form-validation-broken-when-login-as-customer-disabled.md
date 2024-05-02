---
title: '''MDVA-35910: formuliervalidatie verbroken wanneer "Aanmelden als klant" uitgeschakeld is'
description: Met de MDVA-35910-patch wordt het probleem opgelost waarbij de validatie van het formulier voor het maken van een klantenaccount wordt verbroken wanneer de extensie **Aanmelden als klant** is uitgeschakeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35910. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: fa63d725-33f0-4422-bcd5-d62dfee01b65
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-35910: formuliervalidatie verbroken wanneer &quot;Aanmelden als klant&quot; is uitgeschakeld

Met de MDVA-35910-patch wordt het probleem opgelost waarbij de validatie van het formulier voor het maken van een klantenaccount wordt verbroken wanneer de **Aanmelden als klant** extensie is uitgeschakeld. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35910. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.1-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Navigeren naar **Winkels > Configuratie > Klanten**. Uitschakelen **Aanmelden als klant** in de Admin.
1. Onder **Aanmelden als klant**, set **Extensie inschakelen** = *Nee*.
1. Sla Config op en verwijder de cache.
1. Ga terug naar de storefront en klik op **Registreren** (Maak een klantenaccount).
1. Vul het accountformulier in en bevestig of de validatie onder **E-mail bevestigen** werkt of niet.

<u>Verwachte resultaten</u>:

Het aanmaakproces van de klantenaccount wordt zonder fouten voltooid.

<u>Werkelijke resultaten</u>:

Het aanmaakproces van de klantenaccount is niet voltooid en in plaats daarvan worden JavaScript-consolefouten weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
