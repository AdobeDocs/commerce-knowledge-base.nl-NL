---
title: 'ACSD-47497: ontbrekende ACL voor Store/Configuration/Services [!UICONTROL OAuth]'
description: Pas de ACSD-47497-patch toe om het Adobe Commerce-probleem op te lossen wanneer machtigingen voor een bepaalde rol zijn ingesteld en u kunt geen toegang tot de configuratiesectie definiëren.
exl-id: c13fd541-1379-4893-9190-9da1422b2b99
feature: Configuration, Identity Management, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-47497: ontbrekende ACL voor Store/Configuration/Services [!UICONTROL OAuth]

De ACSD-47497-patch lost het probleem op waarbij het tabblad **[!UICONTROL Services]** niet wordt weergegeven in de sectie **[!UICONTROL Configuration]** in Adobe Commerce Admin. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 wordt geïnstalleerd. De patch-id is ACSD-47497. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer machtigingen zijn ingesteld voor een bepaalde rol, kunt u de toegang tot **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** niet definiëren.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de Adobe Commerce-beheerder. Ga naar **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** .
1. Selecteer **[!UICONTROL Role Resources]** in de rol van Beheerders, en reeks **[!UICONTROL Resource Access]** onder **[!UICONTROL Roles Resources]** aan _Douane_, dan alle controledozen. Selecteer **[!UICONTROL Save Role]** .
1. Selecteer **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** . De configuratiesectie **[!UICONTROL OAuth]** is niet beschikbaar.

<u> Verwachte resultaten </u>:

In **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** is de configuratiesectie zichtbaar.

<u> Ware resultaten </u>:

In **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** ontbreekt de configuratiesectie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
