---
title: 'ACSD-52219: Het probleem met het filter voor beheerrasters oplossen in het schakelen tussen bladwijzerweergaven'
description: Pas de ACSD-52219-patch toe om het Adobe Commerce-probleem op te lossen waarbij de opgeslagen filters van de beheerrasters niet werken zoals u had verwacht wanneer vaak wordt geschakeld tussen bladwijzerweergaven.
feature: Admin Workspace
role: Admin
exl-id: e8333ee7-28a8-4457-aeff-6828f8ca9412
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-52219: Het probleem met het filter voor beheerrasters oplossen in het schakelen tussen bladwijzerweergaven

De ACSD-52219-patch verhelpt het probleem waarbij de opgeslagen filters van de beheerrasters niet werken zoals u had verwacht wanneer vaak wordt geschakeld tussen bladwijzerweergaven. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 wordt geïnstalleerd. De patch-id is ACSD-52219. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer vaak wordt geschakeld tussen bladwijzerweergaven, werken de opgeslagen filters in beheerrasters niet naar behoren.

<u> Stappen om </u> te reproduceren:

1. Open het [!DNL Sales Order] -raster in Beheer.
1. Maak twee tot drie filters.
1. Controleer de filterinstellingen door over te schakelen op een andere weergave om te controleren of deze op de juiste wijze zijn opgeslagen.
1. Ga naar Filter1 of Filter2.
1. Vernieuw de pagina om de weergegeven gegevens bij te werken.
1. Schakel over naar een andere weergave. De filters blijven ongewijzigd.
1. In de standaardweergave worden nu de gefilterde resultaten weergegeven, ook al is er geen specifiek filter voor ingesteld.

<u> Verwachte resultaten </u>:

De filters worden niet uitgewisseld en behouden hun oorspronkelijke staat.

<u> Ware resultaten </u>:

Wanneer u een weergave wijzigt, worden de filters gemengd en wordt de juiste weergave niet opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
