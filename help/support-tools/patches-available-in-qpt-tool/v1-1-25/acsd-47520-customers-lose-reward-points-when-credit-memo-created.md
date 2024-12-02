---
title: 'ACSD-47520: klanten verliezen bonuspunten wanneer een creditmemo wordt gemaakt'
description: Pas de ACSD-47520-patch toe om het Adobe Commerce-probleem op te lossen, waarbij klanten beloningspunten verliezen wanneer een creditmemo wordt gemaakt.
exl-id: 748b4e05-981d-49f6-a4f5-b121d57085f4
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47520: klanten verliezen bonuspunten wanneer een creditmemo wordt gemaakt

De ACSD-47520-patch verhelpt het probleem waarbij klanten beloningspunten verliezen wanneer een creditmemo wordt gemaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-47520. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klanten verliezen bonuspunten wanneer een creditmemo wordt gemaakt.

<u> Stappen om </u> te reproduceren:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]** .
1. Wijzig de instelling:
   * **[!UICONTROL Enable Reward Points Functionality]** = _ja_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _ja_
   * **[!UICONTROL Customers May See Reward Points History]** = _ja_
   * **[!UICONTROL Refund Reward Points Automatically]** = _Nr_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _ja_
1. Ga naar Beheer > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** en klik op **[!UICONTROL Add New Rate]** .
1. Voeg nieuwe snelheid (1:1) toe en verwijder de cache.
1. Maak een klant en voeg tien bonuspunten toe aan dit account.
1. Ga naar Beheer > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > Selecteer de klant die u in de vorige stap hebt gemaakt.
1. Selecteer een product waarvan de prijs hoger is dan de bonuspunten.
1. Plaats een bestelling via elke betalingsmethode en de bonuspunten.
1. Maak een factuur voor de bestelling.
1. Maak een creditmemo, maar geef de bonuspunten niet terug.

<u> Verwachte resultaten </u>:

* De beheerder kan de bonuspunten terugbetalen.

* De status van de bestelling wordt gesloten.

<u> Ware resultaten </u>:

* De beloningspunten kunnen niet worden terugbetaald.

* De orderstatus is **[!UICONTROL Completed]** .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
