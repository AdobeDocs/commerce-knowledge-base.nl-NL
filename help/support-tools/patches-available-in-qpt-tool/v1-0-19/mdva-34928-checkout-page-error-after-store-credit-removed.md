---
title: '''MDVA-34928: fout bij het uitchecken van pagina''s nadat winkelkrediet is verwijderd'''
description: De MDVA-34928-patch lost het probleem op waarbij er na het verwijderen van winkelkrediet een oneindige lader op de uitcheckpagina staat. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-34928. De kwestie is opgelost in Adobe Commerce 2.3.6.
exl-id: 9ef6777a-88c8-4fed-a296-0cb4e6ad153a
feature: Checkout, Orders, Returns, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-34928: fout bij het uitchecken van pagina nadat winkelkrediet is verwijderd

De MDVA-34928-patch lost het probleem op waarbij er na het verwijderen van winkelkrediet een oneindige lader op de uitcheckpagina staat. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-34928. De kwestie is opgelost in Adobe Commerce 2.3.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Na het verwijderen van winkelkrediet bevindt zich een oneindige lader op de uitcheckpagina.

<u>Stappen om te reproduceren</u>:

1. Maak een klantenaccount.
1. Bepaal een mogelijk artikel om het winkelwagentje aan te vullen. Noteer de prijs.
1. Bewerk de account in de beheerdersaccount.
1. Klikken **Winkelkrediet**.
1. Voeg een bedrag toe om de prijs van het object te dekken.
1. Meld u aan als de klant in de winkel.
1. Voeg het item aan het winkelwagentje toe.
1. Ga door met de kassa.
1. Pas het winkelkrediet toe.
1. Probeer het winkelkrediet te verwijderen.

<u>Verwachte resultaten</u>:

Winkelkrediet is verwijderd.

<u>Werkelijke resultaten</u>:

Oneindige loader draait totdat de pagina is vernieuwd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
