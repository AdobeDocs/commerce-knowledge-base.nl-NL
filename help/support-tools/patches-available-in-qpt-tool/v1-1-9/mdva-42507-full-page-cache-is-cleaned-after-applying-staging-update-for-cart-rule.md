---
title: 'MDVA-42507: De cache van volledige pagina wordt gereinigd nadat een testupdate voor de kartelregel is toegepast'
description: Met de MDVA-42507-patch wordt het probleem opgelost waarbij de cache van de volledige pagina wordt opgeschoond nadat een testupdate voor de kartelregel is toegepast. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-42507. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 9303d488-428b-4565-b9ea-469c34856dce
feature: Cache, Categories, Orders, Shopping Cart, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42507: De cache van volledige pagina wordt gereinigd nadat een testupdate voor de kartelregel is toegepast

Met de MDVA-42507-patch wordt het probleem opgelost waarbij de cache van de volledige pagina wordt opgeschoond nadat een testupdate voor de kartelregel is toegepast. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 geïnstalleerd is. De patch-id is MDVA-42507. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Cache van volledige pagina wordt schoongemaakt nadat een staging-update voor de kartonregel is toegepast.

<u> Stappen om </u> te reproduceren:

1. Modus voor ontwikkelaars inschakelen.
1. Open verschillende producten en categoriepagina&#39;s en controleer (via kopteksten) of deze vanuit de cache zijn geladen.
1. Pas een testupdate toe voor de kartelregel.
1. Controleer of de categorie- en productpagina&#39;s nog steeds uit de cache worden geladen.

<u> Verwachte resultaten </u>:

Cache van volledige pagina wordt NIET gereinigd nadat een staging-update voor de kartelregel is toegepast.

<u> Ware resultaten </u>:

Cache van volledige pagina wordt schoongemaakt nadat een staging-update voor de kartelregel is toegepast.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
