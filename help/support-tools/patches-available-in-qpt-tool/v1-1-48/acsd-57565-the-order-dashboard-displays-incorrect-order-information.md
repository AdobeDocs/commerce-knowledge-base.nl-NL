---
title: 'ACSD-57565: Het dashboard voor bestellingen bevat onjuiste bestelgegevens'
description: Pas de ACSD-57565-patch toe om het Adobe Commerce-probleem op te lossen, waarbij op het orderdashboard onjuiste bestelgegevens worden weergegeven, totdat de tijdsperiode is bijgewerkt.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 5b292fef-23f6-479f-bf76-adad53d30cf4
source-git-commit: fdf6e6e85f903a26a7b44674937ccf88ee769d06
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57565: op het dashboard voor bestellingen worden onjuiste ordegegevens weergegeven

De ACSD-57565-patch verhelpt het probleem waarbij het orderdashboard onjuiste ordergegevens weergeeft tot de tijdsperiode is bijgewerkt. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.48 is geïnstalleerd. De patch-id is ACSD-57565. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als zoektrefwoord om de patch te zoeken

## Probleem

Het orderdashboard geeft onjuiste ordegegevens weer.

<u>Stappen om te reproduceren</u>:

1. Inschakelen **[!UICONTROL dashboard charts]**.
1. Maak een bestelling en factureer deze.
1. Wacht ten minste 24 uur na het aanmaken van de bestelling.
1. Controleer de **[!UICONTROL dashboard chart]** gegevens.
1. Noteer het totale aantal bestellingen.
1. De tijd wijzigen in de *huidige maand* en wijzig deze vervolgens in *vandaag*.

<u>Verwachte resultaten</u>:

Het dashboarddiagram zou de correcte statistieken moeten voortdurend tonen.

<u>Werkelijke resultaten</u>:

Het dashboarddiagram toont onjuiste statistieken bij de eerste lading. De nauwkeurige statistieken van de grafiek worden na de tijdsperiode bijgewerkt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
