---
title: 'MDVA-32739 patch: old email sent when asynchronous sending enabled'
description: Met de MDVA-32739-patch is het probleem verholpen waarbij [asynchrone e-mailmeldingen] (https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications) oude e-mails worden verzonden. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.2.
exl-id: 8cf4ef8a-f2f2-47fb-9f69-0eedcc10ba8b
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-32739 patch: oude e-mails verzonden wanneer asynchrone verzending ingeschakeld is

De MDVA-32739-patch verhelpt het probleem waarbij [asynchrone e-mailmeldingen](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications) verzendt oude e-mails over verkopen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Schakel asynchrone verzending van e-mail uit.
1. Maak een bestelling en zorg ervoor dat het verzenden van de e-mail mislukt.
1. Schakel asynchroon verzenden in.

<u>Verwachte resultaten</u>:

E-mails worden alleen verzonden voor bestellingen, verzendingen, facturen en creditnota&#39;s die zijn gemaakt na de laatste asynchrone update voor verzenden.

<u>Werkelijke resultaten</u>:

Het oude e-mailbericht wordt verzonden via de opdrachtregel.

## Repareren

Met de moeilijke situatie inbegrepen in de flard, zal Adobe Commerce orden selecteren die worden gecreeerd nadat de asynchrone verzendende methode het laatst is gelopen en zal e-mail voor dergelijke orden verzenden.

Standaard wordt een verschuiving van -1 dag toegepast.

U kunt deze waarde wijzigen (bijvoorbeeld -2 dagen) door `di.xml`.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
