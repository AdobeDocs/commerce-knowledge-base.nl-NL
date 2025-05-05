---
title: 'MDVA-30862: Onjuiste besteldatum op gedrukte PDF factuur'
description: De MDVA-30862-patch verhelpt het probleem waarbij een onjuiste datum van de bestelling op de PDF-factuur wordt afgedrukt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 is geïnstalleerd. De patch-id is MDVA-30862. Deze kwestie is opgelost in Adobe Commerce 2.4.0.
exl-id: 695f530e-6abf-4883-972d-5d9c379493a2
feature: Invoices, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# MDVA-30862: Onjuiste besteldatum op gedrukte PDF factuur

De MDVA-30862-patch verhelpt het probleem waarbij een onjuiste datum van de bestelling op de PDF-factuur wordt afgedrukt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 geïnstalleerd is. De patch-id is MDVA-30862. Deze kwestie is opgelost in Adobe Commerce 2.4.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.4

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.3.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onjuiste besteldatum wordt afgedrukt op de PDF factuur.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Verkoop** > **Orders**.
1. Selecteer een bestelling en druk de factuur af.

<u> Verwachte resultaten </u>:

De datum komt overeen met de aankoopdatum.

<u> Ware resultaten </u>:

De datum (inclusief maand/jaar) komt niet overeen met de aankoopdatum.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
