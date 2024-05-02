---
title: 'MDVA-41236: Kan geen nieuwe geplande updates maken of bewerken voor product'
description: De MDVA-41236-patch verhelpt het probleem dat gebruikers geen nieuwe geplande updates voor het product kunnen maken of bewerken als de "Einddatum" eerder is verwijderd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41236. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 00d6c0af-f248-49f6-aaa2-3ae3c0294832
feature: Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-41236: Kan geen nieuwe geplande updates voor het product maken of bewerken

De MDVA-41236-patch verhelpt het probleem dat gebruikers geen nieuwe geplande updates voor het product kunnen maken of bewerken als de &quot;Einddatum&quot; eerder is verwijderd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41236. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen geen nieuwe schema&#39;s maken of bestaande schema&#39;s voor producten bewerken als de &quot;Einddatum&quot; eerder is verwijderd.

<u>Stappen om te reproduceren</u>:

1. Een product maken met de status ingesteld op *disable*.
1. Voeg een geplande update toe om dit product in te schakelen.
   * Voeg toekomstige begin- en einddatums toe.
1. Bewerk de geplande update door de **Einddatum**.
1. Bewerk het schema opnieuw en probeer een **Einddatum**. Er treedt een fout op.
1. De pagina vernieuwen en nogmaals naar **Geplande update bewerken**.
1. Klikken **Verwijderen uit update** > **De update verwijderen**.
1. De geplande update wordt nu niet weergegeven boven op de productbewerkingspagina.
1. Maak een nieuwe geplande update die de vorige duur overlapt.

<u>Verwachte resultaten</u>:

* Er is geen fout in stap 4. De beheerder kan de geplande update zonder enige fout bijwerken omdat het schema nog niet actief is.
* De beheerder kan de vorige update verwijderen en een nieuwe update maken.

<u>Werkelijke resultaten</u>:

Gebruikers krijgen het volgende foutbericht:

*fout: de toekomstige update bestaat al in dit tijdbereik. Stel een ander bereik in en probeer het opnieuw.*


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
