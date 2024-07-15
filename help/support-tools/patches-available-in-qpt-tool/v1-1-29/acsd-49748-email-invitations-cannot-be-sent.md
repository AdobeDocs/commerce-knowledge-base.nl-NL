---
title: 'ACSD-49748: uitnodigingen via e-mail kunnen niet worden verzonden'
description: Pas de ACSD-49748-patch toe om het Adobe Commerce-probleem op te lossen, waarbij gebruikers geen uitnodigingen via e-mail kunnen verzenden.
exl-id: 65de8ea9-e65c-463b-8cba-d35767d4343d
feature: Admin Workspace, Communications, Marketing Tools
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-49748: e-mailuitnodigingen kunnen niet worden verzonden

De ACSD-49748-patch verhelpt het probleem waarbij gebruikers geen uitnodigingen via e-mail kunnen verzenden. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-49748. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het fout *ging Iets verkeerd terwijl het verzenden van uitnodigingen* verschijnt wanneer het verzenden van uitnodigingen.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Admin Panel]** > **[!UICONTROL Marketing]** > **[!UICONTROL Private Sales]** > **[!UICONTROL Invitations]** .
1. Een uitnodiging maken en opslaan.
1. Ga naar **[!UICONTROL Invitation Grid]** en selecteer een uitnodiging.
1. Verzend de uitnodiging.

<u> Verwachte resultaten </u>:

Er wordt een uitnodiging verzonden wanneer u op *[!UICONTROL Send Invitation]* klikt.

<u> Ware resultaten </u>:

De fout *ging Iets verkeerd terwijl het verzenden van uitnodigingen* verschijnt, en de uitnodiging wordt niet verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.
