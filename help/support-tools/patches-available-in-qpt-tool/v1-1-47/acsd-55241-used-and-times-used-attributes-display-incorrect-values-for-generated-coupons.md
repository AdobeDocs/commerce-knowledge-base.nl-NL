---
title: 'ACSD-55241: **Gebruikte** en **Gebruikte** kenmerken voor Times Used* geven onjuiste waarden weer voor gegenereerde coupons'
description: Pas de ACSD-55241-patch toe om het Adobe Commerce-probleem op te lossen waarbij de kenmerken **Used** en **Times Used** onjuiste waarden weergeven voor gegenereerde coupons
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: 5d0b4743fe49d22c099102490f93dc4065ab4413
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-5241: **Gebruikt** en **Gebruikte tijden** attributen geven onjuiste waarden weer voor gegenereerde coupons

De ACSD-55241-patch verhelpt het probleem waarbij de **Gebruikt** en **Gebruikte tijden** worden onjuiste waarden weergegeven voor gegenereerde coupons. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.47 is geïnstalleerd. De patch-id is ACSD-55241. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

**Gebruikt** en **Gebruikte tijden** worden onjuiste waarden weergegeven voor gegenereerde coupons.

<u>Stappen om te reproduceren</u>:

1. Maken **[!UICONTROL Cart Price Rules]** van **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** en voeg om het even welke voorwaarde toe die tijdens het plaatsen van een orde (Voorbeeld: subtotal groter dan *5$*)

* Pas een willekeurige korting toe.
* Selecteren **[!UICONTROL Auto Coupon]**.
* Er worden enkele coupon-codes gegenereerd op basis van **Couponcodes beheren**.
* Wijzig de index en wis de cache.

1. Een **[!UICONTROL customer account]** en meld u aan bij de frontend.
1. Eén product toevoegen met meer dan *2* hoeveelheden in de kar en één coupon toepassen.
1. Klikken op **[!UICONTROL Check Out with Multiple Addresses]**.
1. Selecteer een afzonderlijk adres voor elk aantal, plaats de orde, en voltooi het controleproces.
1. Neem het ordertotaal van de beheerder waar en zie de toegepaste korting.
1. Plaats een andere order met een andere coupon.
1. Voer de `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` gebruiken om het gebruik van de couponcode bij te werken.

<u>Verwachte resultaten</u>:

Het juiste aantal moet worden weergegeven in het dialoogvenster **Gebruikte tijd** en **Gebruikt** kolommen met **Ja** waarde voor **[!UICONTROL manage coupon]** in de **[!UICONTROL cart price rule]** in de beheerder.

<u>Werkelijke resultaten</u>:

Het gebruikte aantal couponcodes wordt niet bijgewerkt in het dialoogvenster **Gebruikte tijd** in het couponraster en de **Gebruikt** de kolom toont *Nee* waarde als je een bestelling met meerdere verzendadressen plaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
