---
title: 'ACSD-51792: De gebeurtenis Pagina heeft geen indruk'
description: Pas de ACSD-51792-patch toe om het Adobe Commerce-prestatieprobleem op te lossen wanneer een pagina niet de impliciete gebeurtenis heeft wanneer Google Tag Manager 4 is ingeschakeld.
exl-id: 59194d4c-c387-4372-a0ff-1cdd74f8c6df
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51792: De gebeurtenis Pagina heeft geen indruk

De ACSD-51792-patch verhelpt het prestatieprobleem waarbij een pagina niet de impliciete gebeurtenis heeft wanneer [!DNL Google Tag Manager] 4 is ingeschakeld. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51792. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De pagina heeft niet de impressiegebeurtenis wanneer [!DNL Google Tag Manager] 4 is ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** .
1. Configureer de **[!DNL GoogleTag Manager]** -integratie.
1. Ga naar [ de Medewerker van de Markering van Google ](https://tagassistant.google.com/), en voltooi de stappen nodig om met uw website te verbinden.
1. Open een rubriekpagina met een productaanbieding in de winkel.
1. Controleer of de gebeurtenis Impressions zich heeft voorgedaan in de tagassistent-waarnemer.

<u> Verwachte resultaten </u>:

De impressie moet beginnen met alle producten op de pagina.

<u> Ware resultaten </u>:

De pagina heeft niet de impressiegebeurtenis in de Tagassistent-waarnemer.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
