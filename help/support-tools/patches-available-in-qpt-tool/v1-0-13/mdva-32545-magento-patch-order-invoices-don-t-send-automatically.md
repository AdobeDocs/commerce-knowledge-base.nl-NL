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

De patch MDVA-32545 verhelpt het probleem waarbij e-mails met factuur niet automatisch naar de klant worden verzonden voor bestellingen die vanuit de beheerder worden geplaatst. Dit is van invloed op elke betalingsmethode met de **Verkoop** transactietype, zoals **Braintree** of **PayPal Payflow Pro**.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.2-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Elke betalingsmethode inschakelen met de **Verkoop** transactietype. (Bijvoorbeeld: **Braintree** of **PayPal Payflow Pro**.)
1. Maak een eenvoudig product.
1. Maak een klantenaccount op de voorgrond.
1. Plaats een bestelling bij de beheerder.

<u>Verwachte resultaten</u>:

Het e-mailadres van de factuur wordt automatisch naar de klant verzonden, zoals u had verwacht.

<u>Werkelijke resultaten</u>:

Het e-mailadres van de factuur wordt niet automatisch naar de klant verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
