---
title: 'ACSD-49737: coupon wordt onjuist gemarkeerd als gebruikt na een mislukte kaartbetaling.'
description: Pas de ACSD-49737-patch toe om de Adobe Commerce-uitgave te corrigeren waarbij de coupon onjuist is gemarkeerd als gebruikt na een mislukte kaartbetaling.
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737: De coupon wordt verkeerd gemerkt zoals *gebruikt* na een ontbroken kaartbetaling

ACSD-49737 flardfixes de kwestie waar de coupon verkeerd als *wordt gemerkt gebruikt* na een ontbroken kaartbetaling. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 wordt geïnstalleerd. De patch-id is ACSD-49737. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De coupon wordt verkeerd gemerkt zoals *gebruikt* na een ontbroken kaartbetaling.

<u> Eerste vereisten </u>:

1. Configureer de methode **[!UICONTROL Braintree sandbox payment]** .
1. Zorg ervoor de {*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) consument 0} sales.rule.update.coupon.usage opstelling en lopend is.[*

<u> Stappen om </u> te reproduceren:

1. Maak een **[!UICONTROL Cart Price Rule]** met automatisch gegenereerde couponcodes.
1. Meld u aan als klant.
1. Product(en) toevoegen aan de kar.
1. Pas een automatisch gegenereerde couponcode toe.
1. Probeer een bestelling te plaatsen met een mislukte betaling.
1. Controleer het gebruik van de coupon in de **[!UICONTROL Cart Price Rule]** onder het tabblad **[!UICONTROL Manage Coupon Codes]** .

<u> Verwachte resultaten </u>:

Coupon zou niet als *gebruikt* moeten worden gemarkeerd als de betaling wordt ontbroken.

<u> Ware resultaten </u>:

* De code van de coupon zegt - gebruikt: *ja*, Gebruikte Tijden: *1*
* Couponcode is alleen geldig voor eenmalig gebruik.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Aanvullende stappen vereist na de installatie van de patch

(Deze sectie is optioneel; er kunnen enkele stappen vereist zijn na het aanbrengen van de patch om het probleem op te lossen.) 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
