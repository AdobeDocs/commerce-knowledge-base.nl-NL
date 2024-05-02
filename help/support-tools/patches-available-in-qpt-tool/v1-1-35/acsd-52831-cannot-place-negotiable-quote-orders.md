---
title: 'ACSD-52831: Kan geen verhandelbare aanhalingstekenorders plaatsen wanneer [!DNL Google reCAPTCHA v3 Invisible] enabled'
description: Pas de ACSD-52831-patch toe om het Adobe Commerce-probleem op te lossen, waarbij u geen verhandelbare prijsbestellingen kunt plaatsen wanneer [!DNL Google reCAPTCHA v3 Invisible] is ingeschakeld.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: 80cf5592-0784-4b37-8373-abec0847a9f0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52831: kan geen verhandelbare prijsbestellingen plaatsen wanneer [!DNL Google reCAPTCHA v3 Invisible] enabled

Met de ACSD-52831-patch kunt u het probleem verhelpen dat u geen verhandelbare aanhalingstekenorders kunt plaatsen als [!DNL Google reCAPTCHA v3 Invisible] is ingeschakeld. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-52831. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Niet in staat om verhandelbare aanhalingstekens te plaatsen wanneer [!DNL Google reCAPTCHA v3 Invisible] is ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Schakel de functie voor het aanhalingsteken B2B in.
1. Inschakelen [!DNL Google reCAPTCHA v3 Invisible] in de winkel om het uitchecken/plaatsen van bestellingen in te schakelen.
1. Verhoog een aanhalingsteken en ga door met het afrekenen met dat citaat.
1. U kunt geen bestelling plaatsen vanwege de CAPTCHA-fout.

<u>Verwachte resultaten</u>:

Het citaat gaat te werk aan kassa.

<u>Werkelijke resultaten</u>:

De fout verschijnt *reCAPTCHA-validatie mislukt. Probeer het opnieuw*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
