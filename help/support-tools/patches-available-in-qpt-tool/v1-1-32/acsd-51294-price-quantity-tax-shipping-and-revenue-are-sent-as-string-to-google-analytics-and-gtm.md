---
title: '"ACSD-51294: Prijs, hoeveelheid, belasting, verzending, omzet verzonden als tekenreeks aan [!DNL Google Analytics] en GTM'''
description: Pas de ACSD-51294-patch toe om het Adobe Commerce-probleem op te lossen, waarbij prijs, hoeveelheid, belasting, verzending en inkomsten als een tekenreeks worden verzonden naar [!DNL Google Analytics] en GTM.
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 159e1e98-0def-4b20-901d-f5f58c3ead7c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51294: Prijs, hoeveelheid, belasting, verzending, omzet verzonden als tekenreeks aan [!DNL Google Analytics] en GTM

Met de ACSD-51294-patch wordt het probleem opgelost waarbij prijs, hoeveelheid, belasting, verzending en inkomsten als een tekenreeks worden verzonden naar [!DNL Google Analytics] en GTM. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.32 is geïnstalleerd. De patch-id is ACSD-51294. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Prijs, hoeveelheid, belasting, verzending en inkomsten worden als een tekenreeks verzonden naar [!DNL Google Analytics] en GTM.

<u>Stappen om te reproduceren</u>:

1. Configureren [!DNL Google Tag Manager] door naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**.
2. Maak een eenvoudig product.
3. Voltooi het afrekenen met dat product.
4. Controleer de `dataLayer` JavaScript-variabele op de pagina met succesmeldingen bij uitchecken.

<u>Verwachte resultaten</u>

De prijs en het aantal zijn numerieke waarden.

<u>Werkelijke resultaten</u>

Prijs- en kwantitatieve waarden zijn tekenreeksen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
