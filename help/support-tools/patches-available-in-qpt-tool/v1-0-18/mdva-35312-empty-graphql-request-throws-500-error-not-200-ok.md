---
title: 'MDVA-35312: leeg GraphQL-verzoek genereert 500 fout in plaats van 200 OK'
description: De patch MDVA-35312 verhelpt het probleem waarbij een leeg GraphQL-verzoek foutantwoordcode 500 genereert. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is MDVA-35312. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 345fdbd4-8a43-4aab-a318-72792c8a7a78
feature: GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# MDVA-35312: leeg GraphQL-verzoek genereert 500 fout en geen 200 OK

De patch MDVA-35312 verhelpt het probleem waarbij een leeg GraphQL-verzoek foutantwoordcode 500 genereert. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is MDVA-35312. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor versie van Magento:**

Adobe Commerce over wolkeninfrastructuur 2.4.2

**Compatibel met Magento&#39;s versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.4.1-p1-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Lege GraphQL-aanvraag genereert foutantwoordcode 500 in plaats van 200 code.

<u>Stappen om te reproduceren</u>:

Verzend bijvoorbeeld een GraphQL-aanvraag:

```curl
curl -i -X OPTIONS http://inv.test/graphql
```

<u>Verwachte resultaten</u>:

Reactie: *200 OK*.

<u>Werkelijke resultaten</u>:

Reactie: *HTTP/1.1 500 Interne serverfout*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
