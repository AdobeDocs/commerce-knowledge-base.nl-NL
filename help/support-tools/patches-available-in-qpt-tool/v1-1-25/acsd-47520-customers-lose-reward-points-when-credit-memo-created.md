---
title: "ACSD-47520: klanten verliezen bonuspunten wanneer een creditmemo wordt gemaakt"
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

De ACSD-47520-patch verhelpt het probleem waarbij klanten beloningspunten verliezen wanneer een creditmemo wordt gemaakt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 is geïnstalleerd. De patch-id is ACSD-47520. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klanten verliezen bonuspunten wanneer een creditmemo wordt gemaakt.

<u>Stappen om te reproduceren</u>:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. Wijzig de instelling:
   * **[!UICONTROL Enable Reward Points Functionality]** = _Ja_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _Ja_
   * **[!UICONTROL Customers May See Reward Points History]** = _Ja_
   * **[!UICONTROL Refund Reward Points Automatically]** = _Nee_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _Ja_
1. Ga naar Beheer > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** en klik op **[!UICONTROL Add New Rate]**.
1. Voeg nieuwe snelheid (1:1) toe en verwijder de cache.
1. Maak een klant en voeg tien bonuspunten toe aan dit account.
1. Ga naar Beheer > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > Selecteer de klant die u in de vorige stap hebt gemaakt.
1. Selecteer een product waarvan de prijs hoger is dan de bonuspunten.
1. Plaats een bestelling via elke betalingsmethode en de bonuspunten.
1. Maak een factuur voor de bestelling.
1. Maak een creditmemo, maar geef de bonuspunten niet terug.

<u>Verwachte resultaten</u>:

* De beheerder kan de bonuspunten terugbetalen.

* De status van de bestelling wordt gesloten.

<u>Werkelijke resultaten</u>:

* De beloningspunten kunnen niet worden terugbetaald.

* De orderstatus is **[!UICONTROL Completed]**.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
