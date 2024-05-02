---
title: 'ACSD-50345: reCAPTCHA-problemen tijdens het uitchecken'
description: Pas de ACSD-50345-patch toe om het Adobe Commerce-probleem op te lossen waarbij de reCAPTCHA v2- en v3-validaties zijn mislukt tijdens het plaatsen van orders en tijdens het uitchecken.
exl-id: ac8c8130-0e4d-4610-9a55-afa779cce7a0
feature: Checkout, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-50345: reCAPTCHA-problemen tijdens het uitchecken

De ACSD-50345-patch verhelpt het probleem waarbij de reCAPTCHA v2- en v3-validaties mislukken tijdens het plaatsen van orders en tijdens het uitchecken. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31 is geïnstalleerd. De patch-id is ACSD-50345. De kwestie is gedeeltelijk opgelost in Adobe Commerce 2.4.6 en zal volgens de planning volledig worden opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

**Case #1**

Google reCAPTCHA v2 wordt niet opnieuw geladen na het verzenden van een mislukte betaling.

<u>Stappen om te reproduceren</u>

1. Configureren **[!UICONTROL Google reCAPTCHA v2]** (*Ik ben geen robot*).
1. De optie **[!UICONTROL reCAPTCHA]** voor afhandeling.
1. Probeer een bestelling te plaatsen zonder op te klikken **[!UICONTROL reCAPTCHA]**.
1. Zodra de gebruiker het foutbericht voor de ontbrekende reCAPTCHA ontvangt (*reCAPTCHA-validatie mislukt. Probeer het opnieuw*), klikt u op de knop **[!UICONTROL reCAPTCHA]** en probeer vervolgens een bestelling te plaatsen.

<u>Verwachte resultaten</u>

De volgorde wordt niet met een onjuiste reCAPTCHA geplaatst.

<u>Werkelijke resultaten</u>

Er is een fout opgetreden - *reCAPTCHA-validatie mislukt. Probeer het opnieuw* en *Karretje met id = 4*

**Case #2**

Google reCAPTCHA v3 Invisible werkt niet aan uitchecken en de volgorde kan niet worden geplaatst. `PlaceOrder` wordt niet geactiveerd.

<u>Stappen om te reproduceren</u>

1. Vorm **[!UICONTROL reCAPTCHA v3 Invisible]** van de **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Inschakelen **[!UICONTROL reCAPTCHA v3 Invisible]** voor het afrekenen/plaatsen van een bestelling onder **[!UICONTROL Storefront]** tab.
1. Probeer een bestelling te plaatsen bij de [!UICONTROL Check/Money order] betalingsmethode.

<u>Verwachte resultaten</u>

De volgorde moet bij de **[!UICONTROL reCAPTCHA]** ingeschakeld.

<u>Werkelijke resultaten</u>

Nadat u op de knop **[!UICONTROL Place Order]** wordt de knop uitgeschakeld en gebeurt er verder niets.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
