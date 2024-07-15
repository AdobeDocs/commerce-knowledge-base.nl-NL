---
title: 'ACSD-46767: [!UICONTROL Category] pagina in cache wordt ongeldig gemaakt wanneer de voorraadhoeveelheid verandert'
description: Pas de ACSD-46767-patch toe om het Adobe Commerce-probleem op te lossen waarbij de [!UICONTROL Category] -pagina in cache wordt geplaatst, ongeldig wordt wanneer de voorraadhoeveelheid verandert, zelfs als het product nog in voorraad is.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 39811c03-8518-4975-a128-31537b4706c0
source-git-commit: b7e2ff7cd259963adb9a113eb8e94acdaa45ba1e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category] paginacache wordt ongeldig gemaakt wanneer de voorraadhoeveelheid verandert

De ACSD-46767-patch verhelpt het probleem waarbij de cachegeheugen van de [!UICONTROL Category] -pagina ongeldig wordt als de voorraadhoeveelheid verandert, zelfs als het product nog in voorraad is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 wordt geïnstalleerd. De patch-id is ACSD-46767. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!UICONTROL Category] pagina caches ongeldig wanneer het voorraadaantal verandert.

<u> Stappen om </u> te reproduceren:

1. Maak enkele producten en voeg deze toe aan dezelfde categorie.
1. Open de pagina *[!UICONTROL Category]* in de winkel om te controleren of de pagina in de cache is opgeslagen.
1. Plaats de orde met één van de producten van de categorie *(de producthoeveelheid wordt veranderd, maar het product is nog in voorraad)*.
1. Open de pagina [!UICONTROL Category] opnieuw in de winkelruimte.

<u> Ware Resultaten </u>:

De pagina wordt niet vanuit de cache geladen. Het wordt opnieuw gegenereerd.

<u> Verwachte Resultaten </u>:

De pagina wordt uit de cache geladen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
