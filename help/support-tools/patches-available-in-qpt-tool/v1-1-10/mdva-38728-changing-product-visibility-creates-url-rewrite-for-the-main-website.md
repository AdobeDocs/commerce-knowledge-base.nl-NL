---
title: 'MDVA-38728: Als u de zichtbaarheid van een product wijzigt, wordt de URL voor het wijzigen van de hoofdwebsite gewijzigd.'
description: Met de MDVA-38728-patch wordt het probleem opgelost waarbij door het wijzigen van de productzichtbaarheid van de tweede website een URL voor herschrijven van de hoofdwebsite wordt gemaakt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-38728. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: ad1d5f82-294d-485d-acd3-28c3cd0fbf56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-38728: Als u de zichtbaarheid van een product wijzigt, wordt de URL voor het wijzigen van de hoofdwebsite gewijzigd.

Met de MDVA-38728-patch wordt het probleem opgelost waarbij door het wijzigen van de productzichtbaarheid van de tweede website een URL voor herschrijven van de hoofdwebsite wordt gemaakt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-38728. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u de productzichtbaarheid van de tweede website wijzigt, wordt de URL voor het wijzigen van de hoofdwebsite gewijzigd.

<u>Stappen om te reproduceren</u>:

1. Maak een extra website, winkel en winkelvoorvertoning.
1. Maak een eenvoudig product.
1. De zichtbaarheid instellen op **Niet afzonderlijk zichtbaar**.
1. Alleen product toewijzen aan de tweede website.
1. Vul alle andere vereiste velden in.
1. Sla het product op.
1. MySQL-wachtrijen starten:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. Ga naar de productlijst.
1. Selecteer het gemaakte product en werk het zichtbaarheidskenmerk bij met behulp van de massatoeage die u wilt bijwerken naar Catalog en Search.
1. Controleer of de URL is herschreven.

<u>Verwachte resultaten</u>:

Het herschrijven wordt gemaakt voor de tweede website waaraan het product is toegewezen.

<u>Werkelijke resultaten</u>:

Het herschrijven wordt gemaakt voor de hoofdwebsite.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
