---
title: 'MDVA-40601: Kan geen gegevens ophalen over een categorie die is gewijzigd door een geplande update via GraphQL'
description: De MDVA-40601 Adobe Commerce-kwaliteitspatch verhelpt het probleem dat gebruikers een fout krijgen wanneer ze informatie over een categorie wijzigen via een geplande update via GraphQL. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 is geïnstalleerd. De patch-id is MDVA-40601. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: b1ea93e7-8d4a-4bdd-8267-cc60de25bd39
feature: Categories, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-40601: Kan geen gegevens ophalen over categorie gewijzigd via geplande update via GraphQL

De MDVA-40601 Adobe Commerce-kwaliteitspatch verhelpt het probleem dat gebruikers een fout krijgen wanneer ze informatie over een categorie wijzigen via een geplande update via GraphQL. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 is geïnstalleerd. De patch-id is MDVA-40601. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.3.3 en 2.4.2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers krijgen een fout wanneer ze proberen informatie op te halen over een categorie die is gewijzigd door een geplande update via GraphQL.

<u>Stappen om te reproduceren</u>:

1. Stel een categoriestructuur in met een subcategorie zoals hieronder beschreven:

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category
   </code>
   </pre>

1. GraphQL-query uitvoeren met ID 49 &quot;Some Categorie&quot;.

   <pre>
    <code class="language-graphql">
    query {
     category(id: 49) {
      name
      children {
        name
       }
     }
   }
   </code>
   </pre>

   Resultaat

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "category": {
          "name": "Some category",
          "children": [
            {
              "name": "Some child category"
            }
          ]
        }
      }
    }
    </code>
    </pre>

1. Maak een update voor &#39;Een rubriek&#39; met een andere rubrieknaam.
1. Wacht tot de planningupdate is geactiveerd.
1. Voer dezelfde query uit als hierboven is opgegeven.

<u>Verwachte resultaten</u>:

Je ontvangt hetzelfde resultaat, maar dan met de bijgewerkte categorienaam.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op:

<pre>
<code class="language-graphql">
{
  "errors": [
    {
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "category"
      ]
    }
  ],
  "data": {
    "category": null
  }
}
</code>
</pre>

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over kwaliteitspatches voor Adobe Commerce:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
