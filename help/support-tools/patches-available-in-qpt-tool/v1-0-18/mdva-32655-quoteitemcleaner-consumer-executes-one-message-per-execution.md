---
title: '''MDVA-32655: De consument "quoteItemCleaner"voert één bericht per uitvoering uit"'
description: De patch MDVA-32655 corrigeert de onjuiste status van het "lopende" bericht aan het correcte "volledige"bericht voor consument "quoteItemCleaner"na het schrappen van verscheidene producten. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is 32655. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: 07213430-f779-4a53-89fd-bc3905e13675
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32655: De consument &quot;quoteItemCleaner&quot;voert één bericht per uitvoering uit

Met de MDVA-32655-patch wordt de onjuiste status van het bericht &quot;in uitvoering&quot; gecorrigeerd voor het juiste &quot;complete&quot; bericht voor de consument `quoteItemCleaner` na het verwijderen van meerdere producten. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is 32655. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.3

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `quoteItemCleaner` de consument voert bij elke uitvoering slechts één bericht uit.

<u>Stappen om te reproduceren</u>:

1. Controleer de `queue_message_status` databasetabel en zorg ervoor dat alle bestaande wachtrijberichten de status &quot;Voltooid&quot; hebben (status-id 4).
1. Stop de automatische uitvoering van Adobe Commerce-uitsnede.
1. Maak twee of drie eenvoudige producten.
1. Doe een massa schrapping op deze drie eenvoudige producten.
1. In de `queue_message_status` de lijst u ziet er drie nieuwe verslagen voor `catalog_product_removed_queue` onderwerp met status ID 2 (nieuwe record).
1. Voer de volgende opdracht uit om deze in behandeling te nemen `catalog_product_removed_queue` berichten:

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u>Verwachte resultaten</u>:

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

Alle `catalog_product_removed_queue` berichtstatussen worden bijgewerkt om te worden voltooid (ID=4).

<u>Werkelijke resultaten</u>:

Slechts één record van de drie wordt bijgewerkt naar de status &quot;Voltooid&quot; (ID = 4). De status van de andere twee berichten is status ID = 3 (bezig). Een achterstand wordt geproduceerd met onverwerkte rijberichten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
