---
title: 'ACSD-57565: op het dashboard voor bestellingen worden onjuiste ordegegevens weergegeven'
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

De ACSD-57565-patch verhelpt het probleem waarbij het orderdashboard onjuiste ordergegevens weergeeft tot de tijdsperiode is bijgewerkt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-57565. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als zoektrefwoord om de patch te zoeken

## Probleem

Het orderdashboard geeft onjuiste ordegegevens weer.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL dashboard charts]** in.
1. Maak een bestelling en factureer deze.
1. Wacht ten minste 24 uur na het aanmaken van de bestelling.
1. Controleer de **[!UICONTROL dashboard chart]** -gegevens.
1. Noteer het totale aantal bestellingen.
1. Verander de tijd in de *huidige maand*, en verander het dan terug naar *vandaag*.

<u> Verwachte resultaten </u>:

Het dashboarddiagram zou de correcte statistieken moeten voortdurend tonen.

<u> Ware resultaten </u>:

Het dashboarddiagram toont onjuiste statistieken bij de eerste lading. De nauwkeurige statistieken van de grafiek worden na de tijdsperiode bijgewerkt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
