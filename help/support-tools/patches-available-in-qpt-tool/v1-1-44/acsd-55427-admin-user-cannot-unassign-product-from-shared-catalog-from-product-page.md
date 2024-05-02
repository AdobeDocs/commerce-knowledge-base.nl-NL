---
title: "ACSD-55427: een beheerder kan de toewijzing van een product niet ongedaan maken uit **[!UICONTROL Product in Shared Catalogs]** op de productpagina"
description: Pas de ACSD-55427-patch toe om het Adobe Commerce-probleem op te lossen waarbij de toewijzing van een product niet ongedaan kan worden gemaakt vanaf **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427: een beheerder kan het toewijzen van een product niet ongedaan maken **[!UICONTROL Product in Shared Catalogs]** op de productpagina

De ACSD-55427-patch verhelpt het probleem waarbij u de toewijzing van een product niet ongedaan kunt maken **[!UICONTROL Product in Shared Catalogs]** op de productpagina in de catalogus in Commerce Admin. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 is geïnstalleerd. De patch-id is ACSD-55427. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

U kunt de toewijzing van een product niet ongedaan maken **[!UICONTROL Product in Shared Catalogs]** op de productpagina in de catalogus in Commerce Admin.

<u>Stappen om te reproduceren</u>:

Vereisten: Adobe Commerce geïnstalleerd met zowel B2B als **[!UICONTROL Shared Catalogs]** ingeschakeld.
1. Maak een product.
1. Navigeer naar het gedeelde catalogusdashboard en open de standaard gedeelde catalogus.
1. Het product toewijzen aan de standaardcatalogus en een lagere prijs dan de productprijs instellen.
1. Sla de gedeelde catalogus op.
1. Voer de [!UICONTROL CRON] de consumenten/indexen bij te werken.
1. Open het product en verwijder het product onder **[!UICONTROL Product in Shared Catalogs]** sectie.

<u>Verwachte resultaten</u>:

Het product moet onder **[!UICONTROL Product in Shared Catalogs]** sectie.

<u>Werkelijke resultaten</u>:

Het product wordt nog steeds weergegeven in het dialoogvenster **[!UICONTROL Product in Shared Catalogs]** sectie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
