---
title: '"MDVA-44660: Gang accent ["] kan niet worden gebruikt voor de naam van de klant"'
description: Met de MDVA-44660-patch wordt het probleem opgelost waarbij het accent van het graf (`) niet kan worden gebruikt voor de naam van een klant. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-44660. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 696f2690-2af5-4770-a4a8-c88c423c6c16
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# MDVA-44660: Grave accentteken (&grave;) kan niet worden gebruikt voor de naam van de klant

De MDVA-44660-patch verhelpt het probleem waarbij het accent van het graf ligt [\`] kan niet worden gebruikt voor de naam van een klant. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-44660. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het accent wordt ernstig [\`] kan niet worden gebruikt voor de voor- en achternaam van een klant.

<u>Stappen om te reproduceren</u>:

Maak een nieuwe klant van het beheerdersaccount of registreer zich op de Storefront met het accent graf in de voornaam of achternaam, bijvoorbeeld &quot;L&#39;Epicerie&quot;.

<u>Verwachte resultaten</u>:

Er kan een nieuwe klant worden gemaakt met het accent in zijn naam.

<u>Werkelijke resultaten</u>:

*Voornaam is ongeldig!* of *Achternaam is niet geldig* Er wordt een fout weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
