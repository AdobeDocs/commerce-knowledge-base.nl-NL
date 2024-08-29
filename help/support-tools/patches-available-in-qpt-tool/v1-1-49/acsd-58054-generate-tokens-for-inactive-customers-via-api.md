---
title: 'ACSD-58054: genereren van API-token voor inactieve klanten'
description: Pas de ACSD-58054-patch toe om het Adobe Commerce-probleem op te lossen waar het mogelijk is om klanttokens voor inactieve klanten te genereren via de API.
feature: Customers, API Mesh
role: Admin, Developer
source-git-commit: 70f90884d8106719934b007b2e33f033e1b7e2b2
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ACSD-58054: genereren van API-token voor inactieve klanten

De ACSD-58054-patch verhelpt het probleem waarbij het mogelijk is om klanttokens voor inactieve klanten te genereren via de API. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 wordt geïnstalleerd. De patch-id is ACSD-58054. De kwestie zal volgens de planning in B2B 1.5.1 worden opgelost.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Inactieve productie van klanttoken via API.

<u> Eerste vereisten </u>:

De B2B-modules worden geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Maak een klantenaccount.
1. Maak een klanttoken met behulp van API.
1. Navigeer naar de achterkant en schakel de klantenaccount uit.
1. Probeer een klanttoken opnieuw te genereren.

<u> Verwachte resultaten </u>:

Er wordt geen token gegenereerd.

<u> Ware resultaten </u>:

Er wordt een token gegenereerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
