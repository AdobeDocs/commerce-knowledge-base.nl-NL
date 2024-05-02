---
title: "ACSD-48404: *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* veroorzaakt een fout wanneer het drukken van browser achterknoop"
description: Pas de ACSD-48404-patch toe om het Adobe Commerce-probleem op te lossen waar *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* veroorzaakt een fout wanneer het drukken van de browser achterknoop.
exl-id: b4b96198-dee6-4b3c-b60a-0983ef8ef7b2
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-48404: *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* veroorzaakt fout wanneer het drukken van browser achterknoop

De ACSD-48404-patch verhelpt het probleem waarbij: *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* veroorzaakt een fout wanneer het drukken van de browser achterknoop. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-48404. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* veroorzaakt een fout wanneer het drukken van de browser achterknoop.


<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** en stelt de *[!UICONTROL Remember Category Pagination]* tot *Ja*.
1. Open een categorie in de winkel.
1. Selecteer een waarde die niet de standaardwaarde is in het dialoogvenster *[!UICONTROL Show Per Page]* vervolgkeuzelijst. Nadat u een optie hebt geselecteerd, wordt de pagina opnieuw geladen.
1. Nadat de pagina opnieuw is geladen, klikt u op een willekeurig product op de cataloguspagina.
1. Klik op de geopende pagina met productdetails op de knop **[!UICONTROL Back]** van de browser.

<u>Verwachte resultaten</u>:

De cataloguspagina wordt opnieuw geopend.

<u>Werkelijke resultaten</u>:

De categoriepagina retourneert een fout.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
