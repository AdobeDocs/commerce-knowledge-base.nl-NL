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

De ACSD-52133-patch verhelpt het probleem waarbij een klantenaccount niet kan worden opgeslagen na een upgrade. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-52133. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klantenaccount kan niet worden opgeslagen na een upgrade.

<u> Stappen om </u> te reproduceren:

1. Installeer Adobe Commerce versie 2.4.4.
1. Maak een klant.
1. Upgrade Adobe Commerce naar 2.4.6 van de eerdere versie van 2.4.4, waar al een klant is gemaakt.
1. Stel de coderingssleutel in op de onderstaande waarde in `env.php` :

   `d337b914e91ff703b1e94ba4156aadf0`

1. Stel de waarden hieronder in een database in voor elke klant onder de tabel `customer_entity` :

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** .
1. Bewerk de klant waarvoor de bovenstaande waarden zijn bijgewerkt.
1. Klik op **[!UICONTROL Save Customer]** of **[!UICONTROL Save and Continue Edit]**

<u> Verwachte resultaten </u>:

De klant wordt zonder fouten met succes opgeslagen.

<u> Ware resultaten </u>:

* De klantendecord wordt niet opgeslagen.
* Admin ziet het volgende foutenbericht: *iets ging verkeerd terwijl het bewaren van de klant.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
