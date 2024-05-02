---
title: Onzichtbaar [!DNL reCAPTCHA] mislukt tijdens afrekenen, waardoor plaatsing van bestelling wordt voorkomen
description: Pas de ACSD-54656-patch toe om het Adobe Commerce-probleem op te lossen waar het onzichtbare [!DNL reCAPTCHA] werkt niet correct tijdens het afrekenen, wat plaatsing van een bestelling verhindert.
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656: onzichtbaar [!DNL reCAPTCHA] werkt niet correct tijdens het afrekenen, wat plaatsing van een bestelling verhindert.

De ACSD-54656-patch verhelpt het probleem waarbij het onzichtbare [!DNL reCAPTCHA] werkt niet correct tijdens het afrekenen, wat plaatsing van een bestelling verhindert. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 is geïnstalleerd. De patch-id is ACSD-54656. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onzichtbaar [!DNL reCAPTCHA] werkt niet correct tijdens het afrekenen, wat plaatsing van een bestelling verhindert.

<u>Stappen om te reproduceren</u>:

1. Elk type van [!DNL reCAPTCHA] voor een cadeaukaart op de [!UICONTROL Checkout] pagina.
1. Product toevoegen aan winkelwagentje en naar de **[!UICONTROL Checkout]** pagina.
1. Vouw het formulier met de cadeau-kaart uit en vul een geldige coupon in.
1. Klikken op **[!UICONTROL See balance and apply]** knop.

<u>Verwachte resultaten</u>:

Cadeaukaart is toegepast.

<u>Werkelijke resultaten</u>:

Foutbericht wordt weergegeven: *[!DNL reCAPTCHA]validatie mislukt. Probeer het opnieuw*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
