---
title: "ACSD-51379: Wijzigingen in de tekstinhoud van een pagina via [!DNL Page Builder] niet worden opgeslagen"
description: Pas de ACSD-51379-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de wijzigingen in de tekstinhoud van een pagina via [!DNL Page Builder] niet worden opgeslagen.
exl-id: e274ca03-b675-4ded-9820-1d60978685d0
feature: Page Builder, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-51379: wijzigingen in de tekstinhoud van een pagina via [!DNL Page Builder] niet worden opgeslagen

De ACSD-51379-patch verhelpt het probleem waarbij de wijzigingen in de tekstinhoud van een pagina via [!DNL Page Builder] niet worden opgeslagen. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 is geïnstalleerd. De patch-id is ACSD-51379. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De wijzigingen die via [!DNL Page Builder] niet worden opgeslagen.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij Beheer.
1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Maak een testpagina met één rij en één tekstelement op de **[!UICONTROL Content]** tab.
1. De pagina opslaan en terugkeren naar de **[!UICONTROL Content]** tab.
1. Bewerk de tekst door deze te selecteren en te wijzigen.

   **Opmerking:** Het probleem kan alleen worden gereproduceerd als de tekst wordt geselecteerd en gewijzigd zonder dat de editor wordt geactiveerd.

1. Klik op de knop **[!UICONTROL Save and Close]** op de testpagina.
1. Open de testpagina opnieuw en controleer de **[!UICONTROL Content]** tab.

<u>Verwachte resultaten</u>:

De nieuwe tekst wordt opgeslagen voor originele en gedupliceerde tekstelementen.

<u>Werkelijke resultaten</u>:

Het tekstelement is gedupliceerd, maar de nieuwe tekst wordt niet opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
