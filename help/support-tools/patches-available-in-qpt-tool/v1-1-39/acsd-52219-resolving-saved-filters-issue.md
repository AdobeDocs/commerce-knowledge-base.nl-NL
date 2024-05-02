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

De ACSD-52219-patch verhelpt het probleem waarbij de opgeslagen filters van de beheerrasters niet werken zoals u had verwacht wanneer vaak wordt geschakeld tussen bladwijzerweergaven. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 is geïnstalleerd. De patch-id is ACSD-52219. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer vaak wordt geschakeld tussen bladwijzerweergaven, werken de opgeslagen filters in beheerrasters niet naar behoren.

<u>Stappen om te reproduceren</u>:

1. Toegang krijgen tot de [!DNL Sales Order] raster in de beheerder.
1. Maak twee tot drie filters.
1. Controleer de filterinstellingen door over te schakelen op een andere weergave om te controleren of deze op de juiste wijze zijn opgeslagen.
1. Ga naar Filter1 of Filter2.
1. Vernieuw de pagina om de weergegeven gegevens bij te werken.
1. Schakel over naar een andere weergave. De filters blijven ongewijzigd.
1. In de standaardweergave worden nu de gefilterde resultaten weergegeven, ook al is er geen specifiek filter voor ingesteld.

<u>Verwachte resultaten</u>:

De filters worden niet uitgewisseld en behouden hun oorspronkelijke staat.

<u>Werkelijke resultaten</u>:

Wanneer u een weergave wijzigt, worden de filters gemengd en wordt de juiste weergave niet opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
