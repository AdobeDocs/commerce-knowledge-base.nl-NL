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

De ACSD-50345-patch verhelpt het probleem waarbij de reCAPTCHA v2- en v3-validaties mislukken tijdens het plaatsen van orders en tijdens het uitchecken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31 wordt geïnstalleerd. De patch-id is ACSD-50345. De kwestie is gedeeltelijk opgelost in Adobe Commerce 2.4.6 en zal volgens de planning volledig worden opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

**Geval #1**

Google reCAPTCHA v2 wordt niet opnieuw geladen na het verzenden van een mislukte betaling.

<u> Stappen om te reproduceren </u>

1. Vorm **[!UICONTROL Google reCAPTCHA v2]** (*ik ben geen robot*).
1. Schakel **[!UICONTROL reCAPTCHA]** in voor uitchecken.
1. Probeer een bestelling te plaatsen zonder op **[!UICONTROL reCAPTCHA]** te klikken.
1. Zodra de gebruiker het foutenbericht voor ontbrekende reCAPTCHA (*reCAPTCHA ontbroken bevestiging ontvangt, gelieve te proberen opnieuw*), op **[!UICONTROL reCAPTCHA]** te klikken en dan te proberen plaatsend een orde.

<u> Verwachte resultaten </u>

De volgorde wordt niet met een onjuiste reCAPTCHA geplaatst.

<u> Ware resultaten </u>

Een fout wordt geworpen - *reCAPTCHA mislukte bevestiging, gelieve te proberen opnieuw* en *geen zulk karretje met identiteitskaart = 4*

**Geval #2**

Google reCAPTCHA v3 Invisible werkt niet aan uitchecken en de volgorde kan niet worden geplaatst. `PlaceOrder` -gebeurtenis wordt niet geactiveerd.

<u> Stappen om te reproduceren </u>

1. Configureer de lus **[!UICONTROL reCAPTCHA v3 Invisible]** via **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** .
1. Schakel **[!UICONTROL reCAPTCHA v3 Invisible]** in voor het uitchecken/plaatsen van een volgorde onder het tabblad **[!UICONTROL Storefront]** .
1. Plaats een bestelling met de betalingsmethode [!UICONTROL Check/Money order] .

<u> Verwachte resultaten </u>

De volgorde moet worden ingesteld terwijl **[!UICONTROL reCAPTCHA]** is ingeschakeld.

<u> Ware resultaten </u>

Nadat u op de knop **[!UICONTROL Place Order]** hebt geklikt, wordt deze uitgeschakeld en gebeurt er niets meer.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
