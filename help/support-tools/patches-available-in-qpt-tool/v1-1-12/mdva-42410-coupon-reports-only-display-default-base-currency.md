---
title: 'MDVA-42410: Coupon reports only display default base currency'
description: Met de patch MDVA-42410 wordt de emissie gecorrigeerd waarbij de coupon alleen de basisvaluta weergeeft. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-42410. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: b442a2ce-1bd4-4f09-95fd-2c626e32f509
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42410: Coupon reports only display default base currency

Met de patch MDVA-42410 wordt de emissie gecorrigeerd waarbij de coupon alleen de basisvaluta weergeeft. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 geïnstalleerd is. De patch-id is MDVA-42410. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Couponrapporten geven alleen de standaardbasisvaluta weer.

<u> Stappen om </u> te reproduceren:

1. Maak een extra website, winkel en winkelweergave.
1. Stel een andere valuta in voor deze nieuwe website. Bijvoorbeeld Euro.
1. Ga naar **Opslag** > **Wisselkoersen** en vorm munttarieven aan **Euro**.
1. Creeer de Regel van de Prijs van de a **Kar** met een specifieke coupon - **Test**.
1. Ga naar frontend en plaats een orde met de **1&rbrace; coupon van de Test &lbrace;op de nieuwe website.**
1. Ga naar **Rapporten** > **Verkoop** > **Coupons**.
1. Selecteer de nieuwe website in de vervolgkeuzelijst Bereik.
1. Vernieuw statistieken en voer rapporten uit.

<u> Verwachte resultaten </u>:

Couponrapporten geven de valuta van de nieuwe website weer als euro.

<u> Ware resultaten </u>:

Standaardbasisvaluta (in dit geval USD) wordt gebruikt in couponrapporten voor de nieuwe website.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
