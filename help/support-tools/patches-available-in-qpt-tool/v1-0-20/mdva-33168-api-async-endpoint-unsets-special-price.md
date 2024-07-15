---
title: 'MDVA-33168: API async-eindpunt maakt speciale prijs ongedaan'
description: Met de MDVA-33168-patch is het probleem verholpen waarbij het gebruik van het async-eindpunt van de API om een productkenmerk bij te werken een speciale prijs opheft.
exl-id: 4dd26215-b140-4924-8f4d-0d062e5fda2d
feature: REST, Orders, Personalization
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-33168: API async eindpunt unsets special price

Met de MDVA-33168-patch is het probleem verholpen waarbij het gebruik van het async-eindpunt van de API om een productkenmerk bij te werken een speciale prijs opheft.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 geïnstalleerd is. De patch-id is MDVA-33168. Het probleem zal volgens plan worden opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.3-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.3 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Maak twee websites met winkels.
1. Ga naar **Opslag > Configuraties > Catalogus > Catalogus > Prijs > Catalogus** en de Reeks **het Werkingsgebied van de Prijs** = *Website*.
1. Creeer a *tekst-type* productattribuut. Laat alle standaardopties staan.
1. Voeg het gemaakte kenmerk toe aan de standaardkenmerkset.
1. Maak een eenvoudig product voor gebruik met een bundelproduct.
1. Maak een bundelproduct met de volgende voorbeeldopties:
   * **laat Product** toe = *ja*.
   * **Vastgestelde Attributen** = *Gebrek*.
   * **Naam van het Product** = *bundel-1*.
   * **SKU** = *bundel-1*.
   * **Dynamische SKU** = *ja*.
   * **Prijs** = *$100.00*.
   * **de Klasse van de Belasting** = *Belastbare Goederen*.
   * **Status van de Beeld** = *in Voorraad*.
1. Onder **Bundle Punten**, plaats deze opties van het Voorbeeld:
   * **de Punten van de Bundel van de Schip** = *samen*.
   * **Titel van de Optie** = *test*, **Type van Input** = *Keuzerondjes*, **Vereiste** checkbox = *gecontroleerd*.
   * **is Standaard** checkbox = *ongecontroleerd*.
   * **Naam** = *eenvoudig-100*.
   * **SKU** = *eenvoudig-100*.
   * **Prijs** = *100.0*.
   * **Type van Prijs** = *Vast*.
   * **StandaardHoeveelheid** = *1*.
   * **Gebruiker bepaalde** checkbox = *ongecontroleerde*.
1. Schakel het bereik in de niet-standaardopslag en stel de speciale prijs in. (Voorbeeld: op de **Geavanceerde Prijsstelling** pagina, plaats **Speciale Prijs** = *4%*, en **de Mening van de Prijs** = *Waaier van de Prijs*.)
1. Werk het nieuwe attribuut slechts in het niet standaard archiefwerkingsgebied, als dit Voorbeeld bij:

   ```php
       PUT {{base_url}}/rest/en_au/async/V1/products/{{sku}}    {        "product": {            "custom_attributes": [                {                    "attribute_code": "text_attr",                    "value": 21                                   }            ]                    }    }
   ```

<u> Verwachte resultaten </u>:

Andere kenmerkwaarden blijven hetzelfde wanneer een productkenmerk wordt bijgewerkt met de asynchrone API voor rest.

<u> Ware resultaten </u>:

De speciale prijs, die is ingesteld met de asynchrone rest-API onder het bereik van de winkel, wordt verwijderd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
