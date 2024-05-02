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

# ACSD-49737: Coupon wordt ten onrechte gemarkeerd als *gebruikt* na een mislukte kaartbetaling

De ACSD-49737-patch corrigeert de kwestie waar de coupon onjuist is gemarkeerd als *gebruikt* na een mislukte kaartbetaling. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is ACSD-49737. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De coupon is onjuist gemarkeerd als *gebruikt* na een mislukte kaartbetaling.

<u>Vereisten</u>:

1. Vorm **[!UICONTROL Braintree sandbox payment]** methode.
1. Zorg ervoor dat de [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) de consument wordt opgericht en ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Een **[!UICONTROL Cart Price Rule]** met automatisch gegenereerde couponcodes.
1. Meld u aan als klant.
1. Product(en) toevoegen aan de kar.
1. Pas een automatisch gegenereerde couponcode toe.
1. Probeer een bestelling te plaatsen met een mislukte betaling.
1. Controleer het gebruik van de coupon in het dialoogvenster **[!UICONTROL Cart Price Rule]** onder de **[!UICONTROL Manage Coupon Codes]** tab.

<u>Verwachte resultaten</u>:

Coupon mag niet worden gemarkeerd als *gebruikt* als de betaling is mislukt.

<u>Werkelijke resultaten</u>:

* Couponcode zegt: - Gebruikt: *Ja*, Gebruikte tijden: *1*
* Couponcode is alleen geldig voor eenmalig gebruik.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Aanvullende stappen vereist na de installatie van de patch

(Deze sectie is optioneel; er kunnen enkele stappen vereist zijn na het aanbrengen van de patch om het probleem op te lossen.) 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
