---
title: 'MDVA-40545: Alleen het eerste knooppunt voor een pagina wordt opgehaald'
description: Met de MDVA-40545-patch wordt het probleem opgelost waarbij alleen het eerste knooppunt voor een pagina wordt opgehaald, zelfs als er meer dan één knooppunt voor dezelfde pagina is. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-40545. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: ac7aaed9-5e81-45fe-b699-40d9c086a05c
feature: CMS, Cache
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-40545: Alleen het eerste knooppunt voor een pagina wordt opgehaald

Met de MDVA-40545-patch wordt het probleem opgelost waarbij alleen het eerste knooppunt voor een pagina wordt opgehaald, zelfs als er meer dan één knooppunt voor dezelfde pagina is. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 geïnstalleerd is. De patch-id is MDVA-40545. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Alleen het eerste knooppunt voor een pagina wordt opgehaald, zelfs als er meerdere knooppunten voor dezelfde pagina zijn.

<u> Stappen om </u> te reproduceren:

1. In het Admin Comité, ga naar **Hiërarchie** en voeg twee menupunten/knopen toe.
1. Voeg dezelfde CMS-pagina toe aan elk knooppunt.
1. Cache wissen en de voorzijde controleren.
1. Controleer de koppeling en de broodkruimels voor het eerste toegevoegde submenu.
1. Controleer de koppeling en de broodkruimels voor het tweede toegevoegde submenu.

<u> Verwachte resultaten </u>:

Broodkruimels en koppelingen in het tweede submenu zijn relevant voor het tweede knooppunt.

<u> Ware resultaten </u>:

Broodkruimels en koppelingen in het tweede submenu zijn hetzelfde als het eerste submenu.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
