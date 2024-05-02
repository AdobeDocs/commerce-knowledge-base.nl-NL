---
title: 'MDVA-36833: verbroken paginering op pagina met zoekresultaten'
description: De patch MDVA-36833 verhelpt het probleem waarbij paginering wordt onderbroken wanneer de gedeelde catalogus is ingeschakeld en sommige producten zijn uitgesloten van de gedeelde catalogus. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 is geïnstalleerd. De patch-id is MDVA-36833. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: 7105c4ed-48d9-4d4c-bf12-5914bbad62da
feature: Catalog Management, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-36833: verbroken paginering op pagina met zoekresultaten

De patch MDVA-36833 verhelpt het probleem waarbij paginering wordt onderbroken wanneer de gedeelde catalogus is ingeschakeld en sommige producten zijn uitgesloten van de gedeelde catalogus. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.2 is geïnstalleerd. De patch-id is MDVA-36833. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce (alle implementatiemethoden) 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het uitsluiten van bepaalde producten van een gedeelde catalogus leidt tot verbroken paginering voor zoekresultaten.

<u>Stappen om te reproduceren:</u>

1. Gedeelde catalogus inschakelen.
1. Ga naar **Catalogus** > **Gedeelde catalogi** en stelt de standaard Gedeelde Catalogus in door alle producten aan het toe te wijzen.
1. Laad de storefront en zoek naar &quot;jasje&quot;.
1. Noteer de producten op de eerste pagina. Er moeten twaalf producten zijn.
1. Noteer 11 SKU&#39;s van de eerste pagina. Naar back-end gaan en standaard gedeelde catalogus laden.
1. Wijs eerder vermelde SKU&#39;s niet toe vanuit Gedeelde standaardcatalogus.
1. Ga naar de winkel en zoek naar &quot;jasje&quot;.
1. Controleer de eerste pagina van de zoekresultaten.

<u>Werkelijk resultaat:</u>

De eerste pagina heeft één product en de rest van de producten zijn beschikbaar op de tweede pagina.

<u>Verwacht resultaat:</u>

De eerste pagina moet uit twaalf producten bestaan.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.


## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
