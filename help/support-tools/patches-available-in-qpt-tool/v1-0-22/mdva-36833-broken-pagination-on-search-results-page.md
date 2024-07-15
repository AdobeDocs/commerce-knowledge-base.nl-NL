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

De patch MDVA-36833 verhelpt het probleem waarbij paginering wordt onderbroken wanneer de gedeelde catalogus is ingeschakeld en sommige producten zijn uitgesloten van de gedeelde catalogus. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 geïnstalleerd is. De patch-id is MDVA-36833. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce (alle plaatsingsmethodes) 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het uitsluiten van bepaalde producten van een gedeelde catalogus leidt tot verbroken paginering voor zoekresultaten.

<u> Stappen om te reproduceren:</u>

1. Gedeelde catalogus inschakelen.
1. Ga naar **Catalogus** > **Gedeelde Catalogi** en opstelling de standaard Gedeelde Catalogus door alle producten aan het toe te wijzen.
1. Laad de storefront en zoek naar &quot;jasje&quot;.
1. Noteer de producten op de eerste pagina. Er moeten twaalf producten zijn.
1. Noteer 11 SKU&#39;s van de eerste pagina. Naar back-end gaan en standaard gedeelde catalogus laden.
1. Wijs eerder vermelde SKU&#39;s niet toe vanuit Gedeelde standaardcatalogus.
1. Ga naar de winkel en zoek naar &quot;jasje&quot;.
1. Controleer de eerste pagina van de zoekresultaten.

<u> Ware resultaat:</u>

De eerste pagina heeft één product en de rest van de producten zijn beschikbaar op de tweede pagina.

<u> Verwacht resultaat:</u>

De eerste pagina moet uit twaalf producten bestaan.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.


## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
