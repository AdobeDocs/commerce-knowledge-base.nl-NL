---
title: 'MDVA-44887: Fout ''Uncaught SyntaxError: Unexpected token const'' in deelvenster Beheer'
description: 'De patch MDVA-44887 verhelpt het probleem waarbij de beheerder niet op een menuoptie kan klikken. De fout *Uncaught SyntaxError: Unexpected token const* wordt weergegeven in het deelvenster Beheer. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-44887. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.'
exl-id: 66555e66-49d0-4f80-8f77-84ee107ab12e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44887: Fout &#39;Uncaught SyntaxError: Unexpected token const&#39; in deelvenster Beheer

De patch MDVA-44887 verhelpt het probleem waarbij de beheerder niet op een menuoptie kan klikken. De *Uncaught SyntaxError: Onverwachte symbolische const* fout wordt getoond in het Admin paneel. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 geïnstalleerd is. De patch-id is MDVA-44887. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De beheerder kan niet op om het even welke menuoptie klikken. De *Uncaught SyntaxError: Onverwachte symbolische const* fout wordt getoond in het Admin paneel.

<u> Stappen om </u> te reproduceren:

1. JS-bundeling inschakelen.
1. U kunt de JS-bestanden miniateren.
1. Meld u aan bij het deelvenster Commerce Admin.

<u> Verwachte resultaten </u>:

De beheerder kan niet op om het even welke menuoptie klikken. Er is een fout in de browser console: *Uncaught SyntaxError: Unexpected token const*.

<u> Ware resultaten </u>:

Het deelvenster Beheer is toegankelijk voor een beheerder.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
