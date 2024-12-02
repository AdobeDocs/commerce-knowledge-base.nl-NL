---
title: 'ACSD-57315: De nieuwe transactie wordt gecreeerd in  [!DNL PayPal Payflow Pro]  telkens als de haalknoop wordt geklikt'
description: Pas ACSD-57315 flard toe om de kwestie van Adobe Commerce te bevestigen waar een nieuwe transactie in  [!DNL PayPal Payflow Pro]  wordt gecreeerd telkens als de haalknoop op het scherm van de meningstransactie in [!UICONTROL Admin] wordt geklikt.
feature: Payments
role: Admin, Developer
exl-id: bcc7467d-09f9-4235-9f9f-46d3034567b8
source-git-commit: d7ace1f20defb01105d4a241f971b06fca052215
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: Elke keer dat op de knop Ophalen wordt geklikt, wordt in [!DNL PayPal Payflow Pro] een nieuwe transactie gemaakt

De ACSD-57315-patch verhelpt het probleem waarbij elke keer dat op de knop Ophalen wordt geklikt op het scherm met weergavetransacties in [!UICONTROL Admin] een nieuwe transactie wordt gemaakt in [!DNL PayPal Payflow Pro] . Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-57315. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Elke keer dat op de knop Ophalen wordt geklikt op het scherm met weergavetransacties in [!UICONTROL Admin] , wordt in [!DNL PayPal Payflow Pro] een nieuwe transactie gemaakt.

<u> Stappen om </u> te reproduceren:

1. Configureer [!DNL PayPal Payflow Pro].
1. Stel de transactiemethode in op *[!UICONTROL Sale]* .
1. Plaats een orde gebruikend *Kaart van de Krediet*.
1. Open de transactie vanuit [!UICONTROL Admin] .
1. Klik op de knop **[!UICONTROL Fetch]** .
1. Controleer [!DNL PayPal] -account op transacties met betrekking tot de geplaatste order.

<u> Verwachte resultaten </u>:

Er wordt geen nieuwe betalingstransactie gemaakt.

<u> Ware resultaten </u>:

Er wordt een nieuwe betalingstransactie gemaakt voor een bestelling die al is betaald.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
