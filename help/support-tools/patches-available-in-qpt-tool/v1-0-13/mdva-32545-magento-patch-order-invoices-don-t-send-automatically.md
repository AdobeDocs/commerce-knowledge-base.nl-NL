---
title: "MDVA-32545 patch: orderfacturen worden niet automatisch verzonden"
description: De patch MDVA-32545 verhelpt het probleem waarbij e-mails met factuur niet automatisch naar de klant worden verzonden voor bestellingen die vanuit de beheerder worden geplaatst. Dit is van invloed op elke betalingsmethode met het transactietype **Sale**, zoals **Braintree** of **PayPal Payflow Pro**.
exl-id: 682eaeb1-5475-4d37-9536-0605f5b9f163
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# MDVA-32545-patch: bestellingsfacturen worden niet automatisch verzonden

De patch MDVA-32545 verhelpt het probleem waarbij e-mails met factuur niet automatisch naar de klant worden verzonden voor bestellingen die vanuit de beheerder worden geplaatst. Dit beïnvloedt om het even welke betalingsmethode met het **transactietype van de Verkoop**, als **Braintree** of **PayPal Payflow Pro**.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.2-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Laat om het even welke betalingsmethode met het **transactietype van de Verkoop** toe. (Bijvoorbeeld: **Braintree** of **PayPal Payflow Pro**.)
1. Maak een eenvoudig product.
1. Maak een klantenaccount op de voorgrond.
1. Plaats een bestelling bij de beheerder.

<u> Verwachte resultaten </u>:

Het e-mailadres van de factuur wordt automatisch naar de klant verzonden, zoals u had verwacht.

<u> Ware resultaten </u>:

Het e-mailadres van de factuur wordt niet automatisch naar de klant verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
