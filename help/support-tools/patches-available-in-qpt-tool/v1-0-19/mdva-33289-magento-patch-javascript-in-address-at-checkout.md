---
title: 'MDVA-33289 patch: Javascript in address at checkout'
description: Met de MDVA-33289-patch is het probleem verholpen waarbij Javascript tegen betaling een adres weergeeft. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-33289. De kwestie zou volgens de planning in Adobe Commerce 2.4.3 worden opgelost.
exl-id: 247e4f05-7e89-4d37-b3d4-c2cae7595267
feature: Checkout, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-33289 patch: Javascript in address at checkout

Met de MDVA-33289-patch is het probleem verholpen waarbij Javascript tegen betaling een adres weergeeft. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-33289. De kwestie zou volgens de planning in Adobe Commerce 2.4.3 worden opgelost.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:** Adobe Commerce over wolkeninfrastructuur en Adobe Commerce op locatie 2.4.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u uitcheckt met Google Tag Manager (GTM) ingeschakeld, wordt JavaScript weergegeven in het adresveld.

<u>Stappen om te reproduceren</u>:

1. Schakel GTM in. Zie [Google-tagbeheer](https://docs.magento.com/user-guide/marketing/google-tag-manager.html) in onze gebruikershandleiding voor meer informatie.
1. Voeg in de winkel een aantal producten toe aan de winkelwagentje.
1. Uitchecken.

<u>Werkelijk resultaat</u>:

De adressectie wordt bijgewerkt, maar bevat veel Javascript-codetekst.

<u>Verwacht resultaat</u>:

Adres wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
