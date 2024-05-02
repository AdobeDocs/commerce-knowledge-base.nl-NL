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

Inschakelen **Vertexadres opschonen**. Raadpleeg voor stappen [Het vormen de Reiniging van het Adres van Storefront](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.html) in onze gebruikershandleiding.

<u>Stappen om te reproduceren:</u>

1. Maak een account en meld u aan.
1. Een item aan het winkelwagentje toevoegen door op **Toevoegen aan winkelwagentje**. Klik op het pictogram Winkelwagen en klik vervolgens op **Doorgaan naar Afhandeling**.
1. Voer een geldig adres in het dialoogvenster **Verzendadres** veld.
1. Selecteer een van de opties onder **Verzendmethoden**. Klik vervolgens op **Volgende**.
1. Als de Bevestiging van het Adres verschillende adresinformatie voorstelt, klik **Adres bijwerken** en klik op **Volgende**.
1. Schakel het selectievakje **Mijn facturerings- en verzendadres zijn hetzelfde** selectievakje.

<u>Eerste scenario:</u>

Volg de [boven zes stappen](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) en dan:

1. Voer een nieuw geldig factureringsadres in.
1. Klik op de knop **Bijwerken** knop. Het zal het bericht/de suggestie als het volgende tonen: *Het adres is ongeldig.* Hierna volgt een adressuggestie zoals: *Postcode: XXXXX- XXXX Street: XXX City street XXX*
1. Klik op de knop **Bijwerken** (klik niet op de knop **Adres bijwerken** knop Vertex-adressuggestie).
1. Klik op de knop **Bewerken** van het bijgewerkte factureringsadres.
1. Selecteer het adres in de vervolgkeuzelijst Adres.
1. Klik op de knop **Bijwerken** knop.

<u>Verwacht resultaat:</u>

Het oude bericht voor validatie/suggestie wordt verwijderd.

<u>Werkelijk resultaat:</u>

Het validatiebericht/de suggestie *&quot;We hebben geen geldig adres gevonden Postcode : XXXXX-XXXX Street : XXX City street XXX&quot;* bericht is **NOT** verwijderd. Hetzelfde probleem doet zich voor als u een ongeldig adres in het formulier invoert.

<u>Tweede scenario:</u>

Volg de [boven zes stappen](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) en dan:

1. Vul het adresformulier met een geldig adres.
1. Klik op de knop **Bijwerken** knop. Het zal het bericht/de suggestie als het volgende tonen: *Het adres is ongeldig.* Hierna volgt een adressuggestie zoals: *Postcode : XXXXX-XXXX Street : XXX City street XXX*.
1. Klik op de knop **Bijwerken** (klik niet op de knop **Adres bijwerken** knop met suggesties voor hoekpuntadressen).
1. Controleer de ***Mijn facturerings- en verzendadres zijn hetzelfde*** vervolgkeuzelijst.

<u>Verwacht resultaat:</u>

Het oude bericht voor validatie/suggestie wordt verwijderd.

<u>Werkelijk resultaat:</u>

Het validatiebericht/de suggestie *&quot;We hebben geen geldig adres gevonden Postcode: XXXXX-XXXX Street XXX City street XXX&quot;* bericht is **NOT** verwijderd. Hetzelfde probleem doet zich voor als u een ongeldig adres in het formulier invoert.

## Gerelateerde lezing in onze kennisbasis voor ondersteuning:

[Bekende uitgave van Adobe Commerce 2.3.6, 2.4.0-p1 en 2.4.1: kan zich niet aanmelden bij dotdigital wanneer account is ingeschakeld](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
