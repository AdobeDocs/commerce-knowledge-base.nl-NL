---
title: 'MDVA-30945: een fatale fout tijdens het toevoegen en bijwerken van winkelwagentjes'
description: De patch MDVA-30945 lost het probleem op waarbij u een fatale fout *Call aan een lidfunctie getValue() op ongeldig in module-configureerbaar-product CartItemProcessor.php* ontvangt wanneer het bijwerken van kaarten. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.4.2.
exl-id: 0950e91b-900b-421d-91e7-abbfca4f30be
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-30945: een fatale fout tijdens het toevoegen en bijwerken van winkelwagentjes

Het flard MDVA-30945 bevestigt de kwestie waar u een fatale fout *Vraag aan een lidfunctie getValue () op ongeldig in module-configureerbaar-product CartItemProcessor.php* ontvangt wanneer het bijwerken van kaarten. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een fatale PHP fout nadat producten in het winkelwagentje zijn bijgewerkt in Admin.

<u> Stappen om </u> te reproduceren:

1. Maak in Commerce Admin een configureerbaar product zonder opties.
1. Voeg het toe aan het winkelwagentje op de winkel.
1. Ga terug naar Admin, voeg configureerbare opties aan het product toe en sla de veranderingen op.
1. Vernieuw de winkelwagentje pagina.

<u> Verwachte resultaten </u>:

Op de kartpagina, wordt het volgende bevestigingsbericht getoond: *sommige hieronder producten hebben niet alle vereiste opties*.

<u> Ware resultaten </u>:

De startpagina is leeg. In PHP `error.log`, wordt de volgende fout geregistreerd: *Uncaught uitzondering &quot;Error&quot;met bericht &quot;Vraag aan een lidfunctie getValue () op ongeldig&#39; in vendor/magento/module-configurable-product/Model/Quote/Item/CartItemProcessor.php:76*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
