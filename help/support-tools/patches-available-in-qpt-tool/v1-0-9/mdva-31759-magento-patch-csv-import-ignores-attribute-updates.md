---
title: 'MDVA-31759 patch: CSV import negeert attribute updates'
description: De patch MDVA-31759 verhelpt het probleem waarbij bij het importeren van CSV extra kenmerken met de typen *Dropdown* en *Text Area* worden genegeerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 5426866c-893f-4abe-bfbc-6e7b30dd8dab
feature: Attributes, Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-31759 patch: CSV import negeert kenmerkupdates

De MDVA-31759-patch verhelpt het probleem dat bij het importeren van CSV aanvullende kenmerken worden genegeerd *Vervolgkeuzelijst* en *Tekstgebied* typen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bij het importeren van CSV-bestanden worden aanvullende kenmerken genegeerd met *Vervolgkeuzelijst* en *Tekstgebied* typen.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de Commerce-beheerder.
1. Maak een productkenmerk met de volgende configuratie:
   * **Standaardlabel**: *G003*
   * **Invoertype catalogus voor winkeleigenaar**: *Tekstgebied* of *Vervolgkeuzelijst*
   * **Kenmerkcode**: *G003*
   * **Toepassingsgebied**: *Algemeen*
1. Voeg het bovenstaande kenmerk toe aan de standaardkenmerkset.
1. Maak een product met het standaardkenmerk ingesteld en geef een waarde op voor het nieuwe kenmerk.
1. Het product exporteren naar CSV.
1. Werk de kenmerkwaarde bij in het dialoogvenster **extra\_attributes** kolom.
1. Importeer de bijgewerkte CSV.

<u>Verwachte resultaten</u>:

De waarde van het kenmerk G003 wordt bijgewerkt.

<u>Werkelijke resultaten</u>:

De waarde van het kenmerk G003 wordt niet bijgewerkt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
