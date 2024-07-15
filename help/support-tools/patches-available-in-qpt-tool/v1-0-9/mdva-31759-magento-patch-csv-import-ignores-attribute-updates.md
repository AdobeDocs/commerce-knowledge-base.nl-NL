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

Het flard MDVA-31759 lost de kwestie op waar de invoer CSV extra attributen met *Dropdown* en *de types van het Gebied van de Tekst* negeert. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

CSV de invoer negeert extra attributen met *Dropdown* en *de types van het Gebied van de Tekst*.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de Commerce-beheerder.
1. Maak een productkenmerk met de volgende configuratie:
   * **StandaardEtiket**: *G003*
   * **Type van Invoer van de Catalogus voor de Eigenaar van de Opslag**: *Gebied van de Tekst* of *Dropdown*
   * **Code van Attributen**: *G003*
   * **Reikwijdte**: *Globale*
1. Voeg het bovenstaande kenmerk toe aan de standaardkenmerkset.
1. Maak een product met het standaardkenmerk ingesteld en geef een waarde op voor het nieuwe kenmerk.
1. Het product exporteren naar CSV.
1. Werk de attributenwaarde in de **extra \_attributes** kolom bij.
1. Importeer de bijgewerkte CSV.

<u> Verwachte resultaten </u>:

De waarde van het kenmerk G003 wordt bijgewerkt.

<u> Ware resultaten </u>:

De waarde van het kenmerk G003 wordt niet bijgewerkt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
