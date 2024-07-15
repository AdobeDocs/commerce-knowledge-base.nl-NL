---
title: '"ACSD-52831: Kan onderhandelbare citaatorden niet plaatsen wanneer  [!DNL Google reCAPTCHA v3 Invisible]  toegelaten'''
description: Pas ACSD-52831 flard toe om de kwestie van Adobe Commerce te bevestigen waar u geen verhandelbare citaatorden kunt plaatsen wanneer  [!DNL Google reCAPTCHA v3 Invisible]  wordt toegelaten.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: 80cf5592-0784-4b37-8373-abec0847a9f0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52831: kan geen verhandelbare aanhalingstekenorders plaatsen als [!DNL Google reCAPTCHA v3 Invisible] is ingeschakeld

De ACSD-52831-patch verhelpt het probleem dat u geen verhandelbare aanhalingstekenorders kunt plaatsen als [!DNL Google reCAPTCHA v3 Invisible] is ingeschakeld. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-52831. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Kan geen verhandelbare aanhalingstekenorders plaatsen als [!DNL Google reCAPTCHA v3 Invisible] is ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Schakel de functie voor het aanhalingsteken B2B in.
1. Schakel [!DNL Google reCAPTCHA v3 Invisible] in de winkel in om het uitchecken/plaatsen van bestellingen in te schakelen.
1. Verhoog een aanhalingsteken en ga door met het afrekenen met dat citaat.
1. U kunt geen bestelling plaatsen vanwege de CAPTCHA-fout.

<u> Verwachte resultaten </u>:

Het citaat gaat te werk aan kassa.

<u> Ware resultaten </u>:

U krijgt de fout *reCAPTCHA ontbroken bevestiging, gelieve te proberen opnieuw*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
