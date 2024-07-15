---
title: 'ACSD-51149: Gepland [!UICONTROL ImportExport] met ingeschakelde [!UICONTROL Catalog Permissions] maakt indexen ongeldig'
description: Pas de ACSD-51149-patch toe om het probleem met de Adobe Commerce-prestaties op te lossen, waarbij de geplande [!UICONTROL ImportExport] met enabled [!UICONTROL Catalog Permissions] indexen ongeldig maakt.
feature: Cache, Data Import/Export
role: Admin
exl-id: 3a26f4be-8e52-407d-bb25-2841458f3aa5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51149: Gepland [!UICONTROL ImportExport] met ingeschakelde [!UICONTROL Catalog Permissions] maakt indexen ongeldig

De ACSD-51149-patch verhelpt het probleem waarbij de geplande [!UICONTROL ImportExport] met ingeschakelde [!UICONTROL Catalog Permissions] indexen ongeldig maakt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-51149. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gepland [!UICONTROL ImportExport] met ingeschakeld [!UICONTROL Catalog Permissions] maakt de indexen ongeldig.

<u> Stappen om </u> te reproduceren:

1. Schakel *[!UICONTROL Catalog Permissions]* in.
1. Stel alle indexen in op *[!UICONTROL Update by Schedule]* .
1. Maak een eenvoudig product.
1. Exporteer dit product via **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** .
1. Download de geëxporteerde CSV en plaats deze in `<AC root folder>/var/import` .
1. Maak een geplande productimport met de gedownloade CSV.
1. Voer de volledige redex uit.
1. Controleer de status van de indexeerders. Alle indexen moeten de status *[!UICONTROL Ready]* hebben.
1. Voer de gemaakte geplande import uit vanuit het raster.
1. Controleer de status van de indexen opnieuw.

<u> Verwachte resultaten </u>:

Alle indexen hebben de status *[!UICONTROL Ready]* .

<u> Ware resultaten </u>:

Sommige indexen hebben de status *[!UICONTROL Reindex Required]* .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
