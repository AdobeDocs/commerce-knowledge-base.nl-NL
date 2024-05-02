---
title: 'ACSD-52133: Klantenaccount kan niet worden opgeslagen na een upgrade'
description: Pas de ACSD-52133-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een klantenaccount niet kan worden opgeslagen na een upgrade.
feature: Customers, Upgrade
role: Admin
exl-id: 0db7c79e-10e1-4850-81b5-4812fb051941
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-52133: Klantenaccount kan niet worden opgeslagen na een upgrade

De ACSD-52133-patch verhelpt het probleem waarbij een klantenaccount niet kan worden opgeslagen na een upgrade. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-52133. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klantenaccount kan niet worden opgeslagen na een upgrade.

<u>Stappen om te reproduceren</u>:

1. Installeer Adobe Commerce versie 2.4.4.
1. Maak een klant.
1. Upgrade Adobe Commerce naar 2.4.6 van de eerdere versie van 2.4.4, waar al een klant is gemaakt.
1. Stel de coderingssleutel in op de onderstaande waarden `env.php`:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Stel de waarden hieronder in de database in voor alle klanten onder de `customer_entity` tabel:

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Bewerk de klant waarvoor de bovenstaande waarden zijn bijgewerkt.
1. Klikken op **[!UICONTROL Save Customer]** of **[!UICONTROL Save and Continue Edit]**

<u>Verwachte resultaten</u>:

De klant wordt zonder fouten met succes opgeslagen.

<u>Werkelijke resultaten</u>:

* De klantendecord wordt niet opgeslagen.
* De beheerder ziet het volgende foutbericht: *Er is iets misgegaan tijdens het opslaan van de klant.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
