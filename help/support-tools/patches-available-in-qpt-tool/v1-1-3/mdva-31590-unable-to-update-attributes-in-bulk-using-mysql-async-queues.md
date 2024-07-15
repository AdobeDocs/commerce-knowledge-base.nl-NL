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

De patch MDVA-31590 lost de kwestie op waar de gebruikers attributen in bulk kunnen bijwerken gebruikend MySQL async rijen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 geïnstalleerd is. De patch-id is MDVA-31590. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0-2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen attributen niet bulksgewijs bijwerken met MySQL async.

<u> Stappen om </u> te reproduceren:

1. Voer in het productraster op de achtergrond een massale actie uit om de kenmerkwaarden voor een paar producten bij te werken.
   * De producten van de controle en selecteren **Attributen van de Update** van het dropdown van Acties.
1. Stel waarden in voor de vereiste kenmerken en wijs producten toe aan websites en sla deze op.
1. Wanneer de pagina opnieuw wordt geladen, wordt er een bericht als volgt weergegeven:
   *Taak &quot;de attributen van de Update voor N geselecteerde producten&quot;: 1 punt(en) zijn gepland voor een update.*
1. Wacht enkele seconden en laad de achtergrondpagina opnieuw.

<u> Verwachte resultaten </u>:

1. De pagina toont een succesvol updatebericht zoals: *1 punt(en) is met succes bijgewerkt.*
1. Kenmerkwaarden voor verwante producten worden bijgewerkt.
1. In DB worden nieuwe records gemaakt in zowel de tabel `magento_bulk` als de tabel `magento_operation` (bewerkingen die betrekking hebben op de grote hoeveelheid).
1. Nieuwe record(s) worden gemaakt in de tabel `queue_message` (gerelateerd aan de wachtrijen `product_action_attribute.update` en/of `product_action_attribute.website.update` ).
1. `queue_message_status` -tabel bevat records met status &quot;4&quot;.
1. Er zijn GEEN fouten in `system.log`.

<u> Ware resultaten </u>:

1. Op de pagina wordt nog steeds een bericht weergegeven zoals in het volgende voorbeeld:
   *Taak &quot;de attributen van de Update voor N geselecteerde producten&quot;: 1 punt(en) zijn gepland voor een update.*
1. De kenmerkwaarden voor de producten worden bijgewerkt.
1. Een nieuwe record wordt gemaakt in de tabel `message_bulk` , maar er zijn geen verwante record(s) in de tabel `magento_operation` .
1. Nieuwe records worden gemaakt in `queue_message` - en `queue_message_status` -tabellen.
1. `queue_message_status` table has record with error status (status value &quot;6&quot;).
1. `system.log` bevat een fout die lijkt op het volgende:
   *main.CRITICAL: Het bericht is verworpen: SQLSTATE [ 23000 ]: De schending van de integriteitsbeperking: 1048 de Kolom &quot;operation_key&quot;kan ongeldig zijn, de vraag was: TUSSENVOEGSEL IN {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) WAARDEN (?, ?, ?, ?, ?, ?, ?) [][]*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
