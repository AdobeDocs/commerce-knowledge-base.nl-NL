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

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-33168. Het probleem zal volgens plan worden opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.3-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.3 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Maak twee websites met winkels.
1. Ga naar **Winkels > Configuraties > Catalogus > Catalogus > Prijs > Catalogus** en instellen **Prijsbereik** = *Website*.
1. Een *teksttype* productkenmerk. Laat alle standaardopties staan.
1. Voeg het gemaakte kenmerk toe aan de standaardkenmerkset.
1. Maak een eenvoudig product voor gebruik met een bundelproduct.
1. Maak een bundelproduct met de volgende voorbeeldopties:
   * **Product inschakelen** = *Ja*.
   * **Kenmerkset** = *Standaard*.
   * **Productnaam** = *bundel-1*.
   * **SKU** = *bundel-1*.
   * **Dynamische SKU** = *Ja*.
   * **Prijs** = *$ 100,00*.
   * **Belastingklasse** = *Belastbare goederen*.
   * **Status van voorraad** = *In voorraad*.
1. Onder **Bundel-items** stelt u de volgende voorbeeldopties in:
   * **Verzendbundelobjecten** = *Samen*.
   * **Optietitel** = *test*, **Invoertype** = *Keuzerondjes*, **Vereist** checkbox = *ingeschakeld*.
   * **Is standaard** checkbox = *ongecontroleerd*.
   * **Naam** = *simple-100*.
   * **SKU** = *simple-100*.
   * **Prijs** = *100,00*.
   * **Prijssoort** = *Vast*.
   * **Standaardhoeveelheid** = *1*.
   * **Door gebruiker gedefinieerd** checkbox = *ongecontroleerd*.
1. Schakel het bereik in de niet-standaardopslag en stel de speciale prijs in. (Voorbeeld: op het **Geavanceerde prijzen** pagina, set **Speciale prijs** = *4%*, en **Prijsweergave** = *Prijsklasse*.)
1. Werk het nieuwe attribuut slechts in het niet standaard archiefwerkingsgebied, als dit Voorbeeld bij:

   ```php
       PUT {{base_url}}/rest/en_au/async/V1/products/{{sku}}    {        "product": {            "custom_attributes": [                {                    "attribute_code": "text_attr",                    "value": 21                                   }            ]                    }    }
   ```

<u>Verwachte resultaten</u>:

Andere kenmerkwaarden blijven hetzelfde wanneer een productkenmerk wordt bijgewerkt met de asynchrone API voor rest.

<u>Werkelijke resultaten</u>:

De speciale prijs, die is ingesteld met de asynchrone rest-API onder het bereik van de winkel, wordt verwijderd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
