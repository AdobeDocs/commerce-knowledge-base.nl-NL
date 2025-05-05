---
title: 'MDVA-43718: De fout "De consument is niet gemachtigd om tot middelen toegang te hebben"verschijnt wanneer het toegang tot van gedeelde catalogus'
description: De patch MDVA-43718 lost het probleem op waar de fout *consumer geen toegang heeft tot %resources.* wordt weergegeven wanneer u een gedeelde catalogus opent vanuit een aangepaste integratie. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-43718. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: fa783ed4-906e-4ee6-b82a-cfe6db5ae89e
feature: Catalog Management
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43718: De fout &quot;De consument is niet gemachtigd om tot middelen toegang te hebben&quot;verschijnt wanneer het toegang tot van gedeelde catalogus

De flard MDVA-43718 lost de kwestie op waar de fout *consument niet wordt gemachtigd om tot %resources toegang te hebben.* wordt weergegeven wanneer u een gedeelde catalogus opent vanuit een aangepaste integratie. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 geïnstalleerd is. De patch-id is MDVA-43718. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De volgende fout verschijnt wanneer het toegang tot van een gedeelde catalogus van een douaneintegratie: *de consument wordt niet gemachtigd om tot %resources* toegang te hebben.

<u> Stappen om </u> te reproduceren:

1. Creeer een nieuwe integratie van Admin > **Systeem** > **Integratie** > **voegt Integratie** toe.
1. Voeg toegang toe voor de volgende bronnen en activeer de integratie:

   * Magento_SharedCatalog::list
   * Magento_SharedCatalog:manage
   * Magento_catalogus:catalogus

1. De toegang tot de integratie gebruiken: `rest/default/V1/sharedCatalog/1`

<u> Verwachte resultaten </u>:

Details van de gedeelde catalogus worden geretourneerd.

<u> Ware resultaten </u>:

De volgende fout wordt geretourneerd:

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
