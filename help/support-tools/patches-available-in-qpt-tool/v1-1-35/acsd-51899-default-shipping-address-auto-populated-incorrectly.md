---
title: 'ACSD-51899: standaard verzendadres onjuist ingevuld.'
description: Pas de ACSD-51899-patch toe om het Adobe Commerce-probleem op te lossen waarbij het standaardverzendadres automatisch wordt ingevuld met een onjuist adres.
feature: Checkout
role: Admin
exl-id: 67100fcd-e98f-4740-8f1f-fcc820f4c75d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-51899: standaardverzendadres wordt niet correct ingevuld

De ACSD-51899-patch verhelpt het probleem waarbij het standaardverzendadres automatisch wordt ingevuld met een onjuist adres. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-51899. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het standaardverzendadres wordt automatisch ingevuld met een onjuist adres

<u> Stappen om </u> te reproduceren:

1. Laat **in de Bestelwagen van de Opslag** onder het verschepen methode toe.
1. Creeer *voorraad* en *bron*.
1. Maak een product en wijs het product aan de bron toe.
1. Voeg een product toe aan winkelwagentje.
1. Klik op **ga aan Controle** van mini-kar te werk.
1. Ga teste-mailadres in en selecteer **Kiezen in Opslag**.
1. Klik de **Uitgezochte Opslag** knoop, en selecteer een opslagplaats om van te kiezen.
1. Klik op de **volgende** knoop.
1. Navigeer aan de **Pagina van het Huis** door op het opslagembleem te klikken.
1. Open de **Mini kart**.
1. Klik op bodemhyperlink genoemd **Mening en geef Kaart** uit.
1. Klik **ga aan Controle** te werk.
1. Klik op de verzendknop op de verzendpagina.

<u> Verwachte resultaten </u>

Het verschepende adresgebied blijft leeg behalve *Land, Gebied, en Postcode*.

<u> Ware resultaten </u>

Het standaard verschepende adres is auto-bevolkt met *in-opslag bestelwagen* adres na het verfrissen van de pagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
