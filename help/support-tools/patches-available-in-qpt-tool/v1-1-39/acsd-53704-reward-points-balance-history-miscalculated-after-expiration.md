---
title: "ACSD-53704: historie van de balans van de punten in achterwaartse richting, onjuist berekend na afloop"
description: Pas de ACSD-53704-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de geschiedenis van de beloningspunten na de vervaldatum van de bonuspunten onjuist is berekend.
feature: Rewards
role: Admin, Developer
exl-id: 5300cc22-0425-4467-b1e2-8bd799afb5fd
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-53704: Historische waarde van de balans van de punten in achterwaartse richting onjuist berekend na afloop van de looptijd

De ACSD-53704-patch verhelpt het probleem waarbij de geschiedenis van de beloningspunten na de vervaldatum van de beloningspunten onjuist is berekend. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 is geïnstalleerd. De patch-id is ACSD-53704. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De geschiedenis van de beloningspunten wordt verkeerd berekend na de vervaldatum van de beloningspunten.

<u>Stappen om te reproduceren</u>:

1. Maak een klant in de winkel.
1. Voeg beloningspunten toe voor de klant met verschillende vervaldatums.
1. Controleer de `magento_reward_history` tabel en de vervaldatum voor de laatste bonusrecord instellen op een datum in het verleden:

   ```
   UPDATE magento_reward_history SET expired_at_static = '2023-08-24 10:47:38' WHERE history_id = 3;
   ```

1. Controleer het bonusgeschiedenisraster in **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit customer]** > **[!UICONTROL Reward points]** > **[!UICONTROL Reward Points History]** en **[!UICONTROL Reward Points Balance]**.

<u>Verwachte resultaten</u>:

De balans tussen beloningspunten toont alleen de onverlopen punten.

<u>Werkelijke resultaten</u>:

Het saldo van de bonuspunten weerspiegelt het bedrag dat de verlopen punten omvat.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
