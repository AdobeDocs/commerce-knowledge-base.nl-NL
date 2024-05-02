---
title: "MDVA-35197: GraphQL voegt de fout in het karretje toe bij toegevoegde producten uit voorraad"
description: De MDVA-35197-patch verhelpt het probleem dat er een fout optreedt bij het toevoegen aan winkelwagentje met GraphQL als eerder toegevoegde producten uit voorraad raken. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd.
exl-id: 189312f7-a505-4ba4-b12d-662987e69374
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-35197: GraphQL voegt de fout in het karretje toe bij toegevoegde producten uit de voorraad

De MDVA-35197-patch verhelpt het probleem dat er een fout optreedt bij het toevoegen aan winkelwagentje met GraphQL als eerder toegevoegde producten uit voorraad raken. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.6

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Fout bij het toevoegen van een product aan een winkelwagentje via GraphQL als het andere product dat al in de winkelwagentje staat (ook via GraphQL toegevoegd) uit voorraad raakt.

<u>Stappen om te reproduceren</u>:

1. Voeg met GraphQL een willekeurig product toe aan het winkelwagentje.
1. Meld u aan bij het deelvenster Commerce Admin en stel dit product in als een product dat niet in voorraad is.
1. Voeg via GraphQL een ander product aan de winkelwagen toe.

<u>Verwachte resultaten</u>:

Producten in voorraad kunnen aan het karretje worden toegevoegd.

<u>Werkelijke resultaten</u>:

GraphQL-foutbericht: *Sommige producten zijn niet meer in voorraad*. Een nieuw product uit de &quot;voorraad&quot; kan niet worden toegevoegd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
