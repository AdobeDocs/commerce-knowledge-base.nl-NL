---
title: '''ACSD-54972: Canonical category URL don''t update'''
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

De ACSD-54972-patch verhelpt het probleem waarbij de canonieke categorie-URL niet wordt bijgewerkt nadat de categorie-URL is gewijzigd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 is geïnstalleerd. De patch-id is ACSD-54972. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De URL van de canonieke categorie wordt niet bijgewerkt nadat de categorie-URL is gewijzigd.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**.

   * Set *[!UICONTROL Use Canonical Link Meta Tag for Categories]*: *JA*

2. Een categorie maken (bijvoorbeeld *Naam*: *Categorie 01*, *URL-sleutel*: *categorie 01*).
3. Werk de *URL-sleutel* op een andere waarde dan de oorspronkelijke waarde, terwijl de **[!UICONTROL Create Permanent Redirect for old URL]** selectievakje ingeschakeld.
4. Maak de cache leeg.
5. Ga naar de *[!UICONTROL Category Page]* op de voorzijde.
6. Controleer de paginabron en zoek naar de *canonicaal* -tag.

<u>Verwachte resultaten</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u>Werkelijke resultaten</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
