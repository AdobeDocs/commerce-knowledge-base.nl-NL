---
title: 'De kenmerken ACSD-55241: **Gebruikte** en **Gebruikte*** voor het weergeven van onjuiste waarden voor gegenereerde coupons'
description: Pas de ACSD-55241-patch toe om het Adobe Commerce-probleem op te lossen waarbij de kenmerken **Used** en **Times Used** onjuiste waarden weergeven voor gegenereerde coupons
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: f830486ab3b00fca92dda897bbf0bfbae41543c1
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241: **Gebruikte** en **Gebruikte Tijden** attributen tonen onjuiste waarden voor geproduceerde coupons

ACSD-55241 herstelt de flard waar **Gebruikte** en **Gebruikte Tijden** attributen onjuiste waarden voor geproduceerde coupons tonen. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.47 is geïnstalleerd. De patch-id is ACSD-55241. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

**Gebruikte** en **Gebruikte Tijden** attributen tonen onjuiste waarden voor geproduceerde coupons.

<u> Stappen om </u> te reproduceren:

1. Creeer **[!UICONTROL Cart Price Rules]** van **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** en voeg om het even welke voorwaarde toe die terwijl het plaatsen van een orde aanpast (Voorbeeld: subtotaal groter dan *5$*)

   * Pas een willekeurige korting toe.
   * Selecteer **[!UICONTROL Auto Coupon]** .
   * Het zal een paar Codes van de Coupon van **produceren beheert de Codes van de Coupon**.
   * Wijzig de index en wis de cache.

1. Maak een **[!UICONTROL customer account]** en meld u aan bij de voorzijde.
1. Voeg één product met meer dan *2* hoeveelheden in de kar toe en pas één coupon toe.
1. Klik op **[!UICONTROL Check Out with Multiple Addresses]** .
1. Selecteer een afzonderlijk adres voor elk aantal, plaats de orde, en voltooi het controleproces.
1. Neem het ordertotaal van de beheerder waar en zie de toegepaste korting.
1. Plaats een andere order met een andere coupon.
1. Voer de opdracht `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` uit om het gebruik van de couponcode bij te werken.

<u> Verwachte resultaten </u>:

De correcte telling zou in de **Gebruikte Tijd** en **Gebruikte** kolommen met **ja** waarde voor **[!UICONTROL manage coupon]** in **[!UICONTROL cart price rule]** in admin moeten worden getoond.

<u> Ware resultaten </u>:

De gebruikte telling van de couponcode werkt niet in de **Gebruikte Tijd** kolom in het couponnet bij, en de **Gebruikte** kolom toont de *Geen* waarde als u een orde met veelvoudige het verschepen adressen plaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
