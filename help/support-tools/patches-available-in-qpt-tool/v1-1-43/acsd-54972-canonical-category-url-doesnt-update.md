---
title: 'ACSD-54972: URL van canonieke categorie wordt niet bijgewerkt'
description: Pas de ACSD-54972-patch toe om het Adobe Commerce-probleem op te lossen waarbij de canonieke categorie-URL niet wordt bijgewerkt nadat de categorie-URL is gewijzigd.
feature: Catalog Management, Products, Categories
role: Admin, Developer
exl-id: 2d78f5f6-d485-45a4-a40d-9a0ddd124f82
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-54972: URL van canonieke categorie wordt niet bijgewerkt na wijziging van categorie-URL

De ACSD-54972-patch verhelpt het probleem waarbij de canonieke categorie-URL niet wordt bijgewerkt nadat de categorie-URL is gewijzigd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 wordt geïnstalleerd. De patch-id is ACSD-54972. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De URL van de canonieke categorie wordt niet bijgewerkt nadat de categorie-URL is gewijzigd.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** .

   * Plaats *[!UICONTROL Use Canonical Link Meta Tag for Categories]*: *JA*

2. Creeer een categorie (bijvoorbeeld, *Naam*: *Categorie 01*, *Sleutel URL*: *categorie-01*).
3. Werk *Sleutel URL* aan iets verschillend van de originele waarde bij terwijl het houden van **[!UICONTROL Create Permanent Redirect for old URL]** aangekruiste checkbox.
4. Maak de cache leeg.
5. Ga naar de *[!UICONTROL Category Page]* aan de voorkant.
6. Controleer de paginabron en onderzoek naar de *canonieke* markering.

<u> Verwachte resultaten </u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u> Ware resultaten </u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
