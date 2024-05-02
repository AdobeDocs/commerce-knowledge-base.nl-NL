---
title: 'ACSD-49502: Downloadbare koppeling wordt niet correct bijgewerkt na [!DNL staging] update'
description: Pas de ACSD-49502-patch toe om het Adobe Commerce-probleem op te lossen waarbij de downloadbare koppeling niet correct wordt bijgewerkt na een [!DNL staging] update wordt toegepast op het downloadbare product.
exl-id: 9e7f0c06-4b7d-42c4-8ec7-cdeefd7e8a08
feature: Staging
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-49502: Downloadbare koppeling wordt niet correct bijgewerkt na [!DNL staging] update

De ACSD-49502-patch verhelpt het probleem waarbij de downloadbare koppeling niet correct wordt bijgewerkt na een [!DNL staging] update wordt toegepast op het downloadbare product. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-49502. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De downloadbare koppeling wordt niet correct bijgewerkt na een [!DNL staging] update wordt toegepast op het downloadbare product.

<u>Stappen om te reproduceren</u>:

1. Een downloadbaar product maken met een of meer koppelingen.
1. Maak een klantenaccount en meld u aan.
1. Voeg het downloadbare product vanuit de winkel toe aan de winkelwagentje.
1. In de **[!UICONTROL Admin]**, plant een nieuwe update voor het downloadbare product en laat de geplande update voltooien.
1. Voltooi de bestelling op de winkel.

<u>Verwachte resultaten</u>:

Downloadbare koppelingen blijven behouden wanneer geplande updates worden gebruikt terwijl eerder toegevoegde producten zich in het winkelwagentje bevinden.

<u>Werkelijke resultaten</u>:

Downloadbare koppelingen ontbreken zowel onder de *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) en weergavepagina&#39;s in de  **[!UICONTROL Admin]**.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
