---
title: "ACSD-47910: ontbrekende orders, facturen, overbrengingen, creditnota's in de respectieve entiteitsnetwerken"
description: Pas de ACSD-47910-patch toe om het Adobe Commerce-probleem op te lossen wanneer er in de respectievelijke entiteitsnetwerken orders, facturen, verzendingen en creditnota's ontbreken.
exl-id: 4eb897ec-16e4-420e-89a6-c8f7c8740303
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-47910: ontbrekende orders, facturen, overbrengingen en creditnota&#39;s in de respectieve entiteitsnetwerken

De ACSD-47910-patch verhelpt het probleem waarbij orders, facturen, verzendingen en creditnota&#39;s ontbreken in de respectieve entiteitsnetwerken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-47910. De versie waarin dit probleem wordt opgelost, is nog niet beschikbaar.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Ontbrekende orders, facturen, overbrengingen en creditnota&#39;s in de respectieve entiteitsnetwerken.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL Asynchronous indexing]** in **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** .
1. Plaats twee bestellingen.
1. Voer het uitsnijden uit om deze bestellingen te synchroniseren met het raster.
1. Open een van de bestellingen en maak deze gereed om te worden gefactureerd. MAAK DE FACTUUR NOG NIET IN.
1. Maak een nieuwe orde klaar om op de voorzijde te worden geplaatst. KLIK NOG NIET OP DE KNOP VOLGORDE PLAATSEN.
1. Voeg een `sleep(30)` toe in de lus `foreach` at `NotSyncedDataProvider::L43` .
1. Voer `bin/magento cron:run` uit.
1. Plaats nu de nieuwe bestelling.
1. Factuur de vorige bestelling.
1. Voer het uitsnijden opnieuw uit, waarbij u verwacht dat de nieuwe volgorde wordt gesynchroniseerd.
1. Ga naar het orderraster in Beheer.

<u> Verwachte resultaten </u>:

De nieuwe orde zou op het ordennet moeten verschijnen.

<u> Ware resultaten </u>:

De vorige orderupdate is gesynchroniseerd met het raster (**[!UICONTROL status: Processing]**). De nieuwe volgorde wordt nooit op het raster weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
