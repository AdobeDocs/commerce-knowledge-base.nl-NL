---
title: Adobe Commerce 2.4.1 Vertex Bericht voor validatie van hoekpunt Bericht na adresupdate
description: In dit artikel wordt een bekende Adobe Commerce 2.4.1-kwestie beschreven waarbij de validatie van hoekpuntadressen niet werkt tijdens de stap Betaling wanneer een verzendadres wordt gebruikt dat afwijkt van het factuuradres. Het probleem zal volgens planning worden opgelost in Adobe Commerce 2.4.2.
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 Vertex Bericht voor validatie van hoekpunt Bericht na adresupdate

In dit artikel wordt een bekende Adobe Commerce 2.4.1-kwestie beschreven waarbij de validatie van hoekpuntadressen niet werkt tijdens de stap Betaling wanneer een verzendadres wordt gebruikt dat afwijkt van het factuuradres. Het probleem zal volgens planning worden opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.1 met Vertex-integratie ingeschakeld
* Adobe Commerce op cloud-infrastructuur 2.4.1 met Vertex-integratie ingeschakeld

## Probleem

Vereisten:

Laat **Reiniging van het Adres van de top** toe. Voor stappen, verwijs naar [&#x200B; het Vormen het Schoonmaken van het Adres Storefront &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.html?lang=nl-NL) in onze gebruikersgids.

<u> Stappen om te reproduceren:</u>

1. Maak een account en meld u aan.
1. Voeg een punt aan de kar toe door **te klikken toevoegt aan Kaart**. Klik op het pictogram van het Kunst en klik dan **Ga aan Controle** te werk.
1. Ga een geldig adres op het **Verzendadres** gebied in.
1. Controleer één van de opties onder **Verschepende Methoden**. Dan klik **daarna**.
1. Als de Bevestiging van het Adres verschillende adresinformatie voorstelt, klik **adres van de Update** en klik **daarna**.
1. Uncheck **Mijn het factureren en verschepen adres zijn het zelfde** checkbox.

<u> Eerste scenario:</u>

Volg [&#x200B; boven zes stappen &#x200B;](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) en toen:

1. Voer een nieuw geldig factureringsadres in.
1. Klik op de **knoop van de Update**. Het zal het bericht/de suggestie als het volgende tonen: *het adres is ongeldig.* dit zal met een adressuggestie als volgen: *Postcode: XXXXX- XXXX Street: XXX de straat van de Stad*
1. Klik op de **knoop van de Update** (klik niet op de **het adres van de Update** knoop van de het adressuggestie van de Top).
1. Klik op **uitgeven** knoop van het bijgewerkte facturerings adres.
1. Selecteer het adres in de vervolgkeuzelijst Adres.
1. Klik op de **knoop van de Update**.

<u> Verwacht resultaat:</u>

Het oude bericht voor validatie/suggestie wordt verwijderd.

<u> Ware resultaat:</u>

Het bevestigingsbericht/de suggestie *&quot;wij vonden geen geldig adres Postcode: XXXXX-XXXX Street: XXX van de Stad straat XXX&quot;* bericht wordt **NIET** verwijderd. Hetzelfde probleem doet zich voor als u een ongeldig adres in het formulier invoert.

<u> Tweede scenario:</u>

Volg [&#x200B; boven zes stappen &#x200B;](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) en toen:

1. Vul het adresformulier met een geldig adres.
1. Klik op de **knoop van de Update**. Het zal het bericht/de suggestie als het volgende tonen: *het adres is ongeldig.* dit zal met een adressuggestie als volgen: *Postcode: XXXXX-XXXX Straat: XXX de straat XXX van de Stad*.
1. Klik op de **knoop van de Update** (klik niet op de **het adres van de Update** knoop van de suggestie van het hoekpuntadres).
1. Controleer ***Mijn het factureren en verschepen adres zijn het zelfde*** drop-down.

<u> Verwacht resultaat:</u>

Het oude bericht voor validatie/suggestie wordt verwijderd.

<u> Ware resultaat:</u>

Het bevestigingsbericht/de suggestie *&quot;wij vonden geen geldig adres Postcode: XXXXX-XXXX straat XXX van de Stad XXX&quot;* bericht wordt **NIET** verwijderd. Hetzelfde probleem doet zich voor als u een ongeldig adres in het formulier invoert.

## Gerelateerde lezing in onze kennisbasis voor ondersteuning:

[Bekende uitgave van Adobe Commerce 2.3.6, 2.4.0-p1 en 2.4.1: kan zich niet aanmelden bij dotdigital wanneer account is ingeschakeld](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
