---
title: "MDVA-15546: Kolom 'entiteit_id' waarbij de clausule dubbelzinnig is"
description: '"De MDVA-15546-patch lost prestatieproblemen op die mogelijk gerelateerd zijn aan sommige Amazon-extensies. Dit probleem wordt aangegeven door de volgende fout in uitzonderingslogboeken: *where*   *Kolom ''entiteit\\\_id'' in waar de component dubbelzinnig is, query was: SELECT \\"main\\_table\\\".\\*, \\"extension\\_attribute\\_amazon\\_order\\_reference\\_id* \\". Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-15546."'
exl-id: d58c1728-eb7a-49e8-a329-3197f2339b9c
feature: B2B, Commerce Intelligence
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-15546: Kolom &#39;entiteit_id&#39; waar de clausule dubbelzinnig is

De MDVA-15546-patch lost prestatieproblemen op die mogelijk gerelateerd zijn aan sommige Amazon-extensies. Deze kwestie in die door de volgende fout in uitzonderingslogboeken wordt vermeld: *waar*   *De kolom &quot;entiteit\_id&quot;in waar de clausule dubbelzinnig is, de vraag was: SELECT \ &quot;main\_table\&quot;.\*, \&quot;extension\_attribute\_amazon\_order\_reference\_id* \`. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 geïnstalleerd is. De patch-id is MDVA-15546.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.2.5

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Prestatieproblemen die mogelijk verband houden met sommige Amazon-extensies.

<u> Eerste vereisten </u>:

Adobe Commerce opschonen met B2B en Amazon\_Payment.

<u> Stappen om </u> te reproduceren:

1. Ga naar de winkelpagina.
1. Voeg een product toe aan de kar.
1. Wacht of activeer de uitsnijdtaak `flush_preview_quotas` .

<u> Werkelijk resultaat </u>:

Wanneer u `var/log/exception/log` controleert, ziet u de volgende fout:

*`report.ERROR: Cron Jobflush_preview_quotashas an error: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'entity_id' in where clause is ambiguous, query was: SELECT `main_table `.*, ` extension_attribute_amazon_order_reference_id `.` amazon_order_reference_id ` AS ` extension_attribute_amazon_order_reference_id_amazon_order_reference_id `, ` extension_attribute_amazon_order_reference_id `.` quote_id ` AS ` extension_amazon_order_reference_reference_id _id `, ` extension_attribute_amazon_order_reference_id `.` sandbox_simulation_reference ` AS ` extension_attribute_amazon_order_reference_id_sandbox_simulation_reference `, ` extension_attribute_amazon_order_reference_id `.` bevestigde ` AS ` uitbreiding_attribute_amazon_order_reference_id_confirm {13 ` AS ` main_table ` LEFT JOIN ` amazon_quote ` AS ` extension_attribute_amazon_order_reference_id` ON main_table.entity_id = extension_attribute_amazon_order_reference_id.quote_id WHERE ...`*` FROM `

<u> Verwacht resultaat </u>:

De uitsnijdtaak wordt zonder fouten voltooid.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
