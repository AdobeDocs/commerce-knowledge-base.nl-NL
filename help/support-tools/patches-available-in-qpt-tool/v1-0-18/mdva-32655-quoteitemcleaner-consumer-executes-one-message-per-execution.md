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

Met de MDVA-32655-patch wordt de onjuiste status van het bericht &#39;in uitvoering&#39; hersteld naar het juiste &#39;complete&#39; bericht voor de consument `quoteItemCleaner` nadat verschillende producten zijn verwijderd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 geïnstalleerd is. De patch-id is 32655. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.3.3

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `quoteItemCleaner` -consument voert slechts één bericht uit bij elke uitvoering.

<u> Stappen om </u> te reproduceren:

1. Controleer de `queue_message_status` databasetabel en zorg ervoor dat alle bestaande wachtrijberichten de status &quot;Voltooid&quot; hebben (status-id 4).
1. Stop de automatische uitvoering van Adobe Commerce-uitsnede.
1. Maak twee of drie eenvoudige producten.
1. Doe een massa schrapping op deze drie eenvoudige producten.
1. In de tabel `queue_message_status` ziet u dat er drie nieuwe records zijn voor het `catalog_product_removed_queue` -onderwerp met status-id 2 (nieuwe record).
1. Voer de volgende opdracht uit om deze berichten die in behandeling zijn, te verwerken: `catalog_product_removed_queue`

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u> Verwachte resultaten </u>:

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

Alle statussen van het `catalog_product_removed_queue` -bericht worden bijgewerkt en voltooid (ID=4).

<u> Ware resultaten </u>:

Slechts één record van de drie wordt bijgewerkt naar de status &quot;Voltooid&quot; (ID = 4). De status van de andere twee berichten is status ID = 3 (bezig). Een achterstand wordt geproduceerd met onverwerkte rijberichten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
