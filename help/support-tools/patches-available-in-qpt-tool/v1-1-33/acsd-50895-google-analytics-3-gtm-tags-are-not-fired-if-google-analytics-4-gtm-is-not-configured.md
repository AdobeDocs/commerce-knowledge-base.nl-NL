---
title: 'ACSD-50895: [!DNL Google Analytics]  3 GTM de markeringen worden niet in brand gestoken als  [!DNL Google Analytics]  4 GTM niet wordt gevormd'
description: Pas ACSD-50895 flard toe om de kwestie van Adobe Commerce te bevestigen waar  [!DNL Google Analytics]  3 GTM de markeringen niet in brand worden gestoken als  [!DNL Google Analytics]  4 GTM niet wordt gevormd.
role: Admin
exl-id: da48f6f1-a68b-4a9c-a79a-d7bd01b65dc2
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50895: [!DNL Google Analytics] 3 GTM-tags worden niet geactiveerd als [!DNL Google Analytics] 4 GTM niet is geconfigureerd

De ACSD-50895-patch verhelpt het probleem waarbij [!DNL Google Analytics] 3 GTM-tags niet worden geactiveerd als [!DNL Google Analytics] 4 GTM niet is geconfigureerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-50895. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL Google Analytics] 3 GTM-tags worden niet geactiveerd als [!DNL Google Analytics] 4 GTM niet is geconfigureerd.

<u> Stappen om </u> te reproduceren:

1. Meld u aan als beheerder.
1. Laat **[!DNL Google Analytics 3]** en **[!DNL Google Tag Manager]** in **Admin** toe > **Opslag** > **Configuratie** > **Verkoop** > **Google API** > **Googles Analytics**.
1. Schakel **[!DNL Google Analytics 4]** en **[!DNL Google Tag Manager]** niet in.
1. Open de productpagina in de winkelruimte.

<u> Verwachte resultaten </u>:

De GTM-tags worden geactiveerd wanneer alleen **[!DNL Google Analytics]** 3 GTM is ingeschakeld.

<u> Ware resultaten </u>:

De GTM-tags worden niet geactiveerd wanneer **[!DNL Google Analytics]** 4 GTM wordt uitgeschakeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
