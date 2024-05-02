---
title: "ACSD-49286: product dat twee keer aan het winkelwagentje wordt toegevoegd wanneer er meerdere producten-widgets aanwezig zijn"
description: Pas de ACSD-49286-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het product tweemaal aan een winkelwagentje wordt toegevoegd wanneer er meerdere producten op de pagina aanwezig zijn.
exl-id: b1764943-945d-4ef9-9bbe-3f3c8383b5b1
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49286: product dat tweemaal aan het winkelwagentje wordt toegevoegd als er meerdere product-widgets aanwezig zijn

De ACSD-49286-patch verhelpt het probleem waarbij het product tweemaal aan een winkelwagentje wordt toegevoegd als er meerdere producten op de pagina aanwezig zijn. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 is geïnstalleerd. De patch-id is ACSD-49286. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het product wordt twee keer aan een winkelwagentje toegevoegd als er meerdere productwidgets op de pagina aanwezig zijn.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de beheerder en ga naar **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Klik in de sectie Inhoud op **[!UICONTROL Edit]** gebruiken [!DNL Page Builder].
1. Twee rijelementen toevoegen aan **[!UICONTROL Content]**.
1. Voeg producten in beide rijelementen toe.
1. In de eerste rij stelt u de weergave van het product in als [!UICONTROL Product Grid] en selecteer een categorie die u wilt weergeven.
1. In de tweede rij stelt u de weergave van het product in als [!UICONTROL Product Carousel] en selecteer een andere categorie die u wilt weergeven.
1. Ga naar de winkel **[!UICONTROL Home Page]** en voegt u één product toe via Productraster.
1. Nog een product toevoegen uit [!UICONTROL Product Carousel].

<u>Verwachte resultaten</u>:

De hoeveelheid product mag niet worden verdubbeld nadat een product van [!UICONTROL Product Grid].

<u>Werkelijke resultaten</u>:

De hoeveelheid product wordt verdubbeld nadat een product uit het winkelwagentje is toegevoegd [!UICONTROL Product Grid].

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure. 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
