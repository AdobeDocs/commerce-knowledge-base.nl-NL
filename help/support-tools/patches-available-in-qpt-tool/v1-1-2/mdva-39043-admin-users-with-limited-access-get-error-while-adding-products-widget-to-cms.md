---
title: 'MDVA-39043: Admin users get error adding widget to CMS page'
description: De MDVA-39043-patch verhelpt het probleem waarbij beheerders met beperkte toegang een fout krijgen tijdens het toevoegen van de widget "Producten" aan de CMS-pagina. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 is geïnstalleerd. De patch-id is MDVA-39043. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 63057351-e972-4575-9bf0-e818f590b40a
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-39043: Admin-gebruikers krijgen een foutmelding bij het toevoegen van een widget aan de CMS-pagina

De MDVA-39043-patch verhelpt het probleem waarbij beheerders met beperkte toegang een fout krijgen tijdens het toevoegen van de widget &quot;Producten&quot; aan de CMS-pagina. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 geïnstalleerd is. De patch-id is MDVA-39043. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruikers met beperkte toegang krijgen een fout tijdens het toevoegen van de widget &quot;Producten&quot; aan de CMS-pagina.

<u> Stappen om </u> te reproduceren:

1. Meld u bij de back-end aan met de beheerder, maar dan met toegang om inhoud te bewerken.
1. Ga naar **Inhoud** > **Pagina&#39;s**.
1. Open een pagina die u wilt bewerken.
1. Bewerk de inhoud met **Bouwer van de Pagina**.
1. Voeg **widget van het Product** product van **toe voeg inhoud** sectie.
1. Klik **vormen** op **Product** widget.

<u> Verwachte resultaten </u>:

Er wordt geen fout weergegeven.

<u> Ware resultaten </u>:

Het volgende foutbericht wordt ontvangen:

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
