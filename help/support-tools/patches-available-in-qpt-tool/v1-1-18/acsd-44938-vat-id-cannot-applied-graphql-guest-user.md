---
title: 'ACSD-44938: VAT_ID kan niet worden toegepast in GraphQL-aanvraag voor gastgebruiker'
description: De ACSD-44938-patch verhelpt het probleem dat de VAT_ID niet kan worden toegepast in een GraphQL-aanvraag voor een gastgebruiker. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 is geïnstalleerd. De patch-id is ACSD-44938. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 18b3dfa5-b666-491e-a067-526a53294f39
feature: Admin Workspace, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-44938: VAT_ID kan niet worden toegepast in GraphQL-verzoek voor gastgebruiker

De ACSD-44938-patch verhelpt het probleem dat de VAT_ID niet kan worden toegepast in een GraphQL-aanvraag voor een gastgebruiker. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 is geïnstalleerd. De patch-id is ACSD-44938. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

VAT_ID kan niet worden toegepast in een GraphQL-aanvraag voor een gastgebruiker.

<u>Stappen om te reproduceren</u>:

1. Voer de in de [GraphQL-zelfstudie](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-shopping-cart.html) in onze ontwikkelaarsdocumentatie om een gastkar tot stand te brengen.
1. Probeer met GraphQL BTW-ID toe te passen op de gastgebruiker.

<u>Verwachte resultaten</u>:

VAT_ID kan op dezelfde manier worden toegepast als voor een geregistreerde klant. Zie [createCustomerAddress-mutatie](https://devdocs.magento.com/guides/v2.4/graphql/mutations/create-customer-address.html) artikel in onze ontwikkelaarsdocumentatie.

<u>Werkelijke resultaten</u>:

VAT_ID kan niet worden toegepast op een gastgebruiker die GraphQL gebruikt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
