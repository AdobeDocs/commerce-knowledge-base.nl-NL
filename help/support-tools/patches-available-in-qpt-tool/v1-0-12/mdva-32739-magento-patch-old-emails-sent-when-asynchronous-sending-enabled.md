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

Het flard MDVA-32739 lost de kwestie op waar het toelaten van [ asynchrone e-mailberichten ](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications) oude verkoope-mails verzendt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Schakel asynchrone verzending van e-mail uit.
1. Maak een bestelling en zorg ervoor dat het verzenden van de e-mail mislukt.
1. Schakel asynchroon verzenden in.

<u> Verwachte resultaten </u>:

E-mails worden alleen verzonden voor bestellingen, verzendingen, facturen en creditnota&#39;s die zijn gemaakt na de laatste asynchrone update voor verzenden.

<u> Ware resultaten </u>:

Het oude e-mailbericht wordt verzonden via de opdrachtregel.

## Repareren

Met de moeilijke situatie inbegrepen in de flard, zal Adobe Commerce orden selecteren die worden gecreeerd nadat de asynchrone verzendende methode het laatst is gelopen en zal e-mail voor dergelijke orden verzenden.

Standaard wordt een verschuiving van -1 dag toegepast.

U kunt deze waarde wijzigen (bijvoorbeeld -2 dagen) door `di.xml` aan te passen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
