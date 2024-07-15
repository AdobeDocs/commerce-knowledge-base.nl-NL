---
title: 'ACSD-51890: [!UICONTROL Submit review] er kan meerdere keren op de knop worden geklikt.'
description: Pas ACSD-51890 flard toe om de kwestie van Adobe Commerce te bevestigen waar de [!UICONTROL Submit Review] knoop veelvoudige tijden zonder  [!DNL Google reCAPTCHA v3]  bevestiging kan worden geklikt.
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890: u kunt meerdere keren op de knop **[!UICONTROL Submit Review]** klikken zonder **[!DNL Google reCAPTCHA v3]** validatie

>[!NOTE]
>
>Dit flard wordt vervangen door [ ACSD-55112 ](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

De ACSD-51890-patch verhelpt het probleem waarbij meerdere keren op de knop **[!UICONTROL Submit Review]** kan worden geklikt zonder **[!DNL Google reCAPTCHA v3]** -validatie. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-51890. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

U kunt meerdere keren op de knop **[!UICONTROL Submit Review]** klikken zonder de **[!DNL Google reCAPTCHA v3]** -validatie.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!DNL Google reCAPTCHA v3]** in voor de productrevisie.
1. Open de productpagina, navigeer naar de sectie **[!UICONTROL Review]** en controleer of [!DNL reCAPTCHA] zichtbaar is.
1. Vul het revisieformulier in en klik zo snel mogelijk op de knop **[!UICONTROL Submit Review]** .
1. Open de sectie **[!UICONTROL Review]** via Beheer.

<u> Verwachte resultaten </u>

Er worden geen dubbele revisies gemaakt.

<u> Ware resultaten </u>

Er worden dubbele revisies gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] gids.
