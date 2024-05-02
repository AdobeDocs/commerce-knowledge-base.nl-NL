---
title: 'ACSD-52657: Minicart niet bijgewerkt bij tweede storeview die subdomein gebruikt'
description: Pas de ACSD-52657-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de minicart niet wordt bijgewerkt in de tweede storeview die een subdomein gebruikt.
feature: Shopping Cart
role: Admin, Developer
exl-id: d0877a15-800e-4e10-9ace-ebb7f26dbd18
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-52657: Minicart wordt niet bijgewerkt bij de tweede storeview die subdomein gebruikt

De ACSD-52657-patch verhelpt het probleem waarbij de minicart niet wordt bijgewerkt in de tweede storeview die een subdomein gebruikt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 is geïnstalleerd. De patch-id is ACSD-52657. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Minicart wordt niet bijgewerkt in de secundaire storeview die een subdomein gebruikt.

<u>Stappen om te reproduceren</u>:

1. Maak een tweede storeview en configureer een subdomein voor de basis-URL.
1. Werk het cookiedomein bij om het gemeenschappelijke domein te hebben.
1. Voeg in de hoofdwinkel een product toe aan het winkelwagentje.
1. Vernieuw de tweede opslagvoorvertoning en ga vervolgens naar de winkelwagentje pagina.

<u>Verwachte resultaten</u>:

De winkelwagentje en minicart worden bijgewerkt op het subdomein.

<u>Werkelijke resultaten</u>:

Minicart wordt niet bijgewerkt wanneer de secundaire opslag wordt vernieuwd, maar op de winkelpagina ziet u het toegevoegde product en u kunt een bestelling in die sessie plaatsen (`PHPSESSID` cookie wordt gedeeld).

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
