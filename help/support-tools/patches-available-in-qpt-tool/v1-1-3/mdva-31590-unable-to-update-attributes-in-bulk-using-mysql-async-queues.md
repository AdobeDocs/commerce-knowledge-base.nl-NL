---
title: 'MDVA-31590: Kan kenmerken niet bulksgewijs bijwerken met MySQL async-wachtrijen'
description: De patch MDVA-31590 lost de kwestie op waar de gebruikers attributen in bulk kunnen bijwerken gebruikend MySQL async rijen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 is geïnstalleerd. De patch-id is MDVA-31590. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 57db28dd-a739-4a77-927d-6339af4fa4a6
feature: Attributes, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# MDVA-31590: Onbekwaam om attributen in bulk bij te werken gebruikend MySQL async rijen

De patch MDVA-31590 lost de kwestie op waar de gebruikers attributen in bulk kunnen bijwerken gebruikend MySQL async rijen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 is geïnstalleerd. De patch-id is MDVA-31590. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0-2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen attributen niet bulksgewijs bijwerken met MySQL async.

<u>Stappen om te reproduceren</u>:

1. Voer in het productraster op de achtergrond een massale actie uit om de kenmerkwaarden voor een paar producten bij te werken.
   * Producten controleren en selecteren **Kenmerken bijwerken** in het vervolgkeuzemenu Handelingen.
1. Stel waarden in voor de vereiste kenmerken en wijs producten toe aan websites en sla deze op.
1. Wanneer de pagina opnieuw wordt geladen, wordt er een bericht als volgt weergegeven:
   *Taak &quot;Kenmerken bijwerken voor N geselecteerde producten&quot;: 1 item(s) is gepland voor een update.*
1. Wacht enkele seconden en laad de achtergrondpagina opnieuw.

<u>Verwachte resultaten</u>:

1. Op de pagina wordt een updatebericht weergegeven, zoals: *1 item(s) zijn bijgewerkt.*
1. Kenmerkwaarden voor verwante producten worden bijgewerkt.
1. In DB worden nieuwe records gemaakt in beide `magento_bulk` tabel en `magento_operation` tabel (verrichtingen in verband met de bulk).
1. Nieuwe record(s) worden gemaakt in het dialoogvenster `queue_message` tabel (gerelateerd aan de wachtrijen) `product_action_attribute.update` en/of `product_action_attribute.website.update`).
1. `queue_message_status` tabel bevat records met status &quot;4&quot;.
1. Er zijn GEEN fouten in `system.log`.

<u>Werkelijke resultaten</u>:

1. Op de pagina wordt nog steeds een bericht weergegeven zoals in het volgende voorbeeld:
   *Taak &quot;Kenmerken bijwerken voor N geselecteerde producten&quot;: 1 item(s) is gepland voor een update.*
1. De kenmerkwaarden voor de producten worden bijgewerkt.
1. Er wordt een nieuwe record gemaakt in `message_bulk` tabel, maar er zijn geen verwante record(s) in `magento_operation` tabel.
1. Nieuwe records worden gemaakt in `queue_message` en `queue_message_status` tabellen.
1. `queue_message_status` table has record with error status (status value &quot;6&quot;).
1. `system.log` bevat een fout die lijkt op het volgende:
   *main.CRITICAL: Bericht is afgewezen: SQLSTATE[23000]: schending van integriteitsbeperking: 1048 kolom &#39;operation_key&#39; mag niet null zijn, query was: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) WAARDEN (?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?) [][]*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
