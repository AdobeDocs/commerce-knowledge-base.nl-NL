---
title: 'ACSD-51792: Pagina heeft geen impressiegebeurtenis'
description: Pas de ACSD-51792-patch toe om het Adobe Commerce-prestatieprobleem op te lossen wanneer een pagina niet de impliciete gebeurtenis heeft wanneer Google Tag Manager 4 is ingeschakeld.
exl-id: 59194d4c-c387-4372-a0ff-1cdd74f8c6df
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51792: De gebeurtenis Pagina heeft geen indruk

De ACSD-51792-patch verhelpt het prestatieprobleem waarbij een pagina niet de impotentie heeft wanneer [!DNL Google Tag Manager] 4 is ingeschakeld. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51792. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De pagina heeft geen impliciete gebeurtenis wanneer [!DNL Google Tag Manager] 4 is ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**.
1. Vorm **[!DNL GoogleTag Manager]** integratie.
1. Ga naar [Google-tagassistent](https://tagassistant.google.com/)en voltooi de stappen die nodig zijn om verbinding te maken met uw website.
1. Open een rubriekpagina met een productaanbieding in de winkel.
1. Controleer of de gebeurtenis Impressions zich heeft voorgedaan in de tagassistent-waarnemer.

<u>Verwachte resultaten</u>:

De impressie moet beginnen met alle producten op de pagina.

<u>Werkelijke resultaten</u>:

De pagina heeft niet de impressiegebeurtenis in de Tagassistent-waarnemer.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
