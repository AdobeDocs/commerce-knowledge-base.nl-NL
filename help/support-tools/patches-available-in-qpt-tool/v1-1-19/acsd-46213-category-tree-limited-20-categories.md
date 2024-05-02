---
title: "ACSD-46213: aanvraag voor een boomcategorie beperkt tot 20 categorieën"
description: 'De ACSD-46213-patch verhelpt het probleem waarbij de aanvraag voor de categoriestructuur beperkt is tot 20 categorieën. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 is geïnstalleerd. De patch-id is ACSD-46213. '
exl-id: 27a18871-8552-4ecd-9e03-0dc38d037ea0
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-46213: aanvraag voor een boomcategorie beperkt tot 20 categorieën

De ACSD-46213-patch verhelpt het probleem waarbij de aanvraag voor de categoriestructuur beperkt is tot 20 categorieën. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 is geïnstalleerd. De patch-id is ACSD-46213.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.


## Probleem

De aanvraag voor de categoriestructuur is beperkt tot 20 categorieën.

<u>Stappen om te reproduceren</u>:

1. Maak een categorie onder de hoofdcategorie.
1. Maak 24 subcategorieën onder de hoofdcategorie die u in stap 1 hebt gemaakt.
1. Voer het volgende GraphQL-verzoek uit:

   <pre>
    <code class="language-graphql">
    {
      categoryList(filters: { parent_id: { in: ["3"] } }) {
        name
        level
        path
        url_path
        children {
          id
          level
          name
          path
          url_path
          url_key
          children {
            uid
            level
            name
            path
            url_path
            url_key
          }
        }
      }
    }
    </code>
    </pre>

1. Controleer de resultaten.

<u>Verwachte resultaten</u>:

Er staan 24 categorieën.

<u>Werkelijke resultaten</u>:

Er worden slechts 20 rubrieken weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
