---
title: 'MDVA-41399: Kan geen toegang krijgen tot het winkelwagentje beheren als een klant een product aan de wenslijst toevoegt'
description: Met de MDVA-41399-patch wordt het probleem opgelost waarbij beheerders geen toegang hebben tot de pagina Winkelwagentje beheren als een klant een product aan de wenslijst toevoegt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 is geïnstalleerd. De patch-id is MDVA-41399. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 227653c6-2d20-4475-b973-b9fa58db815b
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-41399: Kan geen toegang krijgen tot het winkelwagentje beheren als een klant een product aan de wenslijst toevoegt

Met de MDVA-41399-patch wordt het probleem opgelost waarbij beheerders geen toegang hebben tot de pagina Winkelwagentje beheren als een klant een product aan de wenslijst toevoegt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 geïnstalleerd is. De patch-id is MDVA-41399. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruikers hebben geen toegang tot de pagina Winkelwagentje beheren als een klant een product aan de verlanglijst toevoegt.

<u> Eerste vereisten </u>:

1. Maak twee of meer producten.
1. Maak een klant.
1. Schakel de modus Ontwikkelaar in.

<u> Stappen om </u> te reproduceren:

1. Ga naar Storefront en meld u aan als klant onder de voorwaarden.
1. Voeg een product toe aan de Gewenste lijst.
1. Ga naar het Admin paneel en navigeer aan de gecreeerde klant uitgeeft pagina en klik op **beheren het Vormen Kart** knoop.

<u> Verwachte resultaten </u>:

Admin-gebruiker kan het winkelwagentje beheren.

<u> Ware resultaten </u>:

Admin gebruiker krijgt een foutenmelding: *een fout is voorgekomen. Zie foutenlogboek voor details.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
