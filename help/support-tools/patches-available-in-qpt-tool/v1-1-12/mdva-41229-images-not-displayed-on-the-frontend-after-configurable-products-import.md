---
title: 'MDVA-41229: Afbeeldingen die beschikbaar zijn op de achtergrond worden niet weergegeven op de voorzijde na het importeren van configureerbare producten.'
description: Met de MDVA-41229-patch wordt het probleem opgelost waarbij afbeeldingen die op de achtergrond beschikbaar zijn, niet op de voorzijde worden weergegeven nadat configureerbare producten zijn geïmporteerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-41229. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 69d7374f-9f8b-4ec4-8a7f-135ee06135a3
feature: Data Import/Export, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 2%

---

# MDVA-41229: Afbeeldingen die beschikbaar zijn op de achtergrond worden niet weergegeven op de voorzijde nadat configureerbare producten zijn geïmporteerd

Met de MDVA-41229-patch wordt het probleem opgelost waarbij afbeeldingen die op de achtergrond beschikbaar zijn, niet op de voorzijde worden weergegeven nadat configureerbare producten zijn geïmporteerd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-41229. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2-p2 en 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Afbeeldingen die op de achtergrond beschikbaar zijn, worden niet op de voorzijde weergegeven nadat configureerbare producten zijn geïmporteerd.

<u>Stappen om te reproduceren</u>:

1. Een schone Adobe Commerce installeren.
1. Een aangepast kenmerk toevoegen door naar **Winkels** > **Attributen** > **Product** > **Nieuw kenmerk toevoegen** met de onderstaande instellingen:
   * Eigenschappen:
      * Kenmerkeigenschappen:
         * Standaardlabel: Grootte instellen
         * Invoertype catalogus voor winkeleigenaar: Tekststaal
         * Vereiste waarden: geen
         * Afbeelding van productvoorvertoning bijwerken: Ja
      * Staal beheren (waarden van uw kenmerk):

        | Is standaard | Staal beheerder | Beschrijving beheerder | Standaardstaal voor winkelweergave | Standaardbeschrijving van winkelweergave |
        |---|---|---|---|---|
        | nee | 4 | 4 | 4 | 4 |
        | nee | 24 | 24 | 24 | 24 |
        | nee | 30 | 30 | 30 | 30 |
        | nee | 60 | 60 | 60 | 60 |
        | nee | 68 | 68 | 68 | 68 |
      * Geavanceerde kenmerkeigenschappen:
         * Kenmerkcode: set_size
         * Bereik: Algemeen
         * Unieke waarde: Geen
         * Invoervalidatie voor winkeleigenaar: geen
         * Toevoegen aan kolomopties: Nee
         * Gebruiken in filteropties: Nee
   * Labels beheren:
      * Titels beheren (grootte, kleur, enz.)
         * Standaardweergave winkel: grootte instellen
   * Eigenschappen van Storefront:
      * Gebruiken in zoekopdracht: Ja
      * Zoekdikte: 1
      * Zichtbaar in Geavanceerd zoeken: Nee
      * Vergelijkbaar op Storefront: Ja
      * Gebruiken in gelaagde navigatie: Filterbaar (met resultaten)
      * Gebruiken in gelaagde navigatie met zoekresultaten: Ja
      * Gebruik voor de Voorwaarden van de Regel van de Aanbieding: Nr
      * Zichtbaar op cataloguspagina&#39;s in winkel: Ja
      * Gebruikt in productaanbieding: Ja
      * Gebruikt voor sorteren in productaanbieding: Nee
1. Voeg dit attribuut aan het StandaardAttribuut toe binnen de Groep van de Details van het Product (**Winkels** > **Attributen** > **Kenmerkset**).
1. Download afbeeldingen die zijn ingesteld in de var map in de hoofdmap van Adobe Commerce.
1. Ga naar **Systeem** > **Gegevensoverdracht** > en importeer het bestand met de onderstaande opties:
   * Instellingen importeren:
      * Type entiteit: producten
   * Gedrag bij importeren:
      * Gedrag bij importeren: Toevoegen/Bijwerken
      * Validatiestrategie: stoppen bij fout
      * Aantal toegestane fouten: 1
      * Veldscheiding: `;`
      * Scheidingsteken voor meerdere waarden: `,`
      * Constante kenmerkwaarde: EMPTYVALUE
      * Veldbijlage: uitgeschakeld
   * Te importeren bestand:
      * Te importeren bestand selecteren
      * Afbeeldingsbestandsmap: leeg laten
1. Ga naar winkel naar `/product-set.html` en schakelen tussen verschillende sets. Voor Set Size 24 is er geen galerie.

<u>Verwachte resultaten</u>:

De galerie voor alle eenvoudige producten binnen een configureerbaar product is zichtbaar met alle verwante beelden.

<u>Werkelijke resultaten</u>:

Er is geen galerie voor de producten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
