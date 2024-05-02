---
title: 'MDVA-40175: Keuzerondjes niet weergegeven bij opnieuw ordenen'
description: Met de MDVA-40175-patch wordt het probleem opgelost waarbij de keuzerondjes niet worden weergegeven wanneer gebruikers proberen de volgorde te wijzigen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-40175. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 307c450d-9f53-40b7-b2f5-d867850c043a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40175: Radio buttons not displayed when reorder

Met de MDVA-40175-patch wordt het probleem opgelost waarbij de keuzerondjes niet worden weergegeven wanneer gebruikers proberen de volgorde te wijzigen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-40175. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Keuzerondjes worden niet weergegeven in het gedeelte Betalings- en verzendgegevens wanneer gebruikers de volgorde opnieuw proberen in te stellen.

<u>Vereisten</u>:

1. Er wordt een Customer account aangemaakt met een verzendadres en een factuuradres.
1. Er wordt een eenvoudig product gemaakt.
1. Verschillende leveringsmethoden zijn geconfigureerd.
1. Er wordt ten minste één bestelling gemaakt.

<u>Stappen om te reproduceren</u>:

1. Ga naar het deelvenster Beheer > **Verkoop** > **Orders**.
1. Selecteer de gemaakte volgorde.
1. Klik op de knop **Weergave** koppeling.
1. Klik op de knop **Opnieuw** knop.
1. De pagina omlaag schuiven naar de **Betalings- en verzendgegevens** sectie.
1. Klik op de knop **Klik om de verzendmethode te wijzigen**.

<u>Verwachte resultaten</u>:

De lijst met leveringsmethoden met keuzerondjes wordt weergegeven.

<u>Werkelijke resultaten</u>:

De lijst met leveringsmethoden zonder keuzerondjes wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
