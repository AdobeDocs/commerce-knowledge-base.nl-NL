---
title: 'ACSD-50367: Exporteren van klantadres werkt niet met kenmerk voor meerdere selecties'
description: Pas de ACSD-50367-patch toe om het Adobe Commerce-probleem op te lossen waarbij het exporteren van het klantadres niet werkt wanneer een multi-select **'kenmerk Customer Address`** zonder waarden wordt gemaakt.
exl-id: 688831d4-b49e-48fa-b4db-1328cda09a2b
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-50367: Exporteren van klantadres werkt niet

De ACSD-50367-patch verhelpt het probleem waarbij het adres van de klant niet kan worden geëxporteerd wanneer een multi-select **`Customer Address`** wordt een kenmerk zonder waarden gemaakt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is ACSD-50367. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het exporteren van het adres van de klant werkt niet wanneer een multi-select **`Customer Address`** wordt een kenmerk zonder waarden gemaakt.

<u>Vereisten</u>:

Maak een klant met een adres.

<u>Stappen om te reproduceren</u>:

1. Een multi-select maken **`Customer Address`** kenmerk in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** en selecteert u **`Customer Address`** type entiteit.
1. Exporteer de klantadressen. U zult zien dat niets wordt uitgevoerd.
1. De multi-select verwijderen **`Customer Address`** en exporteer de klantenadressen opnieuw. Dit keer wordt het CSV-bestand van de adressen gegenereerd.

<u>Verwachte resultaten</u>:

De klantenadressen kunnen als Csv- dossier worden uitgevoerd wanneer multi-select **`Customer Address`** wordt gemaakt.

<u>Werkelijke resultaten</u>:

De klantenadressen kunnen niet als Csv- dossier worden uitgevoerd wanneer multi-select **`Customer Address`** wordt gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
