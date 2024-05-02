---
title: "MDVA-44887: 'Uncaught SyntaxError: Unexpected token const' error in Admin panel"
description: "De patch MDVA-44887 verhelpt het probleem waarbij de beheerder niet op een menuoptie kan klikken. De fout *Uncaught SyntaxError: Unexpected token const* wordt weergegeven in het deelvenster Beheer. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-44887. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5."
exl-id: 66555e66-49d0-4f80-8f77-84ee107ab12e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44887: Fout &#39;Uncaught SyntaxError: Unexpected token const&#39; in deelvenster Beheer

De patch MDVA-44887 verhelpt het probleem waarbij de beheerder niet op een menuoptie kan klikken. De *Uncaught SyntaxError: Unexpected token const* Er wordt een fout weergegeven in het deelvenster Beheer. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-44887. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De beheerder kan niet op om het even welke menuoptie klikken. De *Uncaught SyntaxError: Unexpected token const* Er wordt een fout weergegeven in het deelvenster Beheer.

<u>Stappen om te reproduceren</u>:

1. JS-bundeling inschakelen.
1. U kunt de JS-bestanden miniateren.
1. Meld u aan bij het deelvenster Commerce Admin.

<u>Verwachte resultaten</u>:

De beheerder kan niet op om het even welke menuoptie klikken. Er is een fout in de browserconsole: *Uncaught SyntaxError: Unexpected token const*.

<u>Werkelijke resultaten</u>:

Het deelvenster Beheer is toegankelijk voor een beheerder.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
