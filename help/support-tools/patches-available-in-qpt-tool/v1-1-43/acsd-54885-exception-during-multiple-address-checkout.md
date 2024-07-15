---
title: 'ACSD-54885: Uitzondering tijdens uitchecken van meerdere adressen wanneer beheerders zich aanmelden als klant'
description: Pas ACSD-54885 flard toe om de kwestie van Adobe Commerce te bevestigen waar een fout tijdens veelvoudige adrescontrole voorkomt wanneer admin de functionaliteit * [!UICONTROL Login as Customer]* gebruikt.
feature: Checkout
role: Admin, Developer
exl-id: 524ec96b-1465-4673-9fbe-1a9c086b7e87
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54885: Uitzondering tijdens uitchecken van meerdere adressen wanneer beheerders zich aanmelden als klant

De ACSD-54885-patch verhelpt het probleem waarbij een fout optreedt tijdens het uitchecken van meerdere adressen wanneer de beheerder de *[!UICONTROL Login as Customer]* -functionaliteit gebruikt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 wordt geïnstalleerd. De patch-id is ACSD-54885. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een fout op tijdens het uitchecken van meerdere adressen wanneer de beheerder de functie *[!UICONTROL Login as Customer]* gebruikt.

<u> Stappen om </u> te reproduceren:

1. Zorg ervoor dat *[!UICONTROL Login as Customer]* is ingeschakeld. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]** .
1. Maak een eenvoudig product.
1. Maak een nieuwe klantenaccount met een adres.
1. Ga naar de klantenaccount op de achtergrond:

   * Ga naar het **[!UICONTROL Account Information]** lusje, en reeks *[!UICONTROL Allow remote shopping assistance]* = *ja*.
   * Klik op **[!UICONTROL Login as Customer]**.

1. Voeg het product toe aan de winkelwagentje en ga verder met *[!UICONTROL Checkout with multiple addresses]* .
1. Werk het aantal producten bij.
1. Probeer terug te gaan naar het winkelwagentje.

<u> Verwachte resultaten </u>:

U kunt het winkelwagentje bijwerken en het uitchecken van meerdere adressen gebruiken.

<u> Ware resultaten </u>:

Je krijgt de volgende fout wanneer je teruggaat naar het winkelwagentje.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
