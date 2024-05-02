---
title: 'MDVA-43983: Producten die zijn ingesteld als "Niet afzonderlijk zichtbaar" worden weergegeven in zoekresultaten.'
description: Met de MDVA-43983-patch wordt het probleem opgelost waarbij de producten die als "Niet afzonderlijk zichtbaar" zijn ingesteld, nog steeds in de geavanceerde zoekresultaten van de catalogus worden weergegeven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43983. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 2599fb6c-5b27-461b-9740-f586ae7df9f5
feature: Catalog Management, Products, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-43983: De producten die als &quot;Niet afzonderlijk zichtbaar&quot;worden geplaatst verschijnen in onderzoeksresultaten

Met de MDVA-43983-patch wordt het probleem opgelost waarbij de producten die als &quot;Niet afzonderlijk zichtbaar&quot; zijn ingesteld, nog steeds in de geavanceerde zoekresultaten van de catalogus worden weergegeven. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43983. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De producten die als &quot;Niet afzonderlijk zichtbaar&quot;worden geplaatst verschijnen nog in catalogus geavanceerde onderzoeksresultaten.

<u>Stappen om te reproduceren</u>:

1. Een kenmerk maken met **Invoertype catalogus voor winkeleigenaar** als **Vervolgkeuzelijst** of **Visueel staal** (bijvoorbeeld Kleur).
1. Set **Gebruiken in Zoeken** als **Ja** en **Zichtbaar in Geavanceerd zoeken** als **Ja**.
1. Voeg enkele kenmerkopties toe.
1. Producten maken met **Zichtbaarheid** als **Niet afzonderlijk zichtbaar**.
1. Opties voor het kenmerk Kleur toewijzen.
1. Ga naar de **Geavanceerd zoeken in catalogus** pagina op de opslagruimte.
1. Selecteer alleen de optie Kleurkenmerk in het veld Kleurkenmerk en laat de rest van de velden leeg of ongewijzigd.
1. Verzend een geavanceerd zoekformulier.
1. Bekijk de zoekresultaten.

<u>Verwachte resultaten</u>:

Producten die zijn ingesteld als &quot;Niet afzonderlijk zichtbaar&quot;, worden niet weergegeven in de geavanceerde zoekresultaten van de catalogus.

<u>Werkelijke resultaten</u>:

Producten die zijn ingesteld als &quot;Niet afzonderlijk zichtbaar&quot; worden weergegeven in de geavanceerde zoekresultaten van de catalogus.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
