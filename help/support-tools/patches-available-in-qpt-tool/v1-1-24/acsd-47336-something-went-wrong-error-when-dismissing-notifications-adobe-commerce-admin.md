---
title: '"ACSD-47336: [!UICONTROL Something went wrong] fout bij het negeren van meldingen in Adobe Commerce Admin'''
description: Pas de ACSD-47336-patch toe om het Adobe Commerce-probleem op te lossen dat de gebruiker ziet [!UICONTROL Something went wrong] fout bij het negeren van meldingen in het dialoogvenster [!DNL Commerce] Admin.
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-4736: _[!UICONTROL Something went wrong]_fout bij het negeren van meldingen in Adobe Commerce Admin

De ACSD-47336-patch verhelpt het probleem waarbij de gebruiker de _[!UICONTROL Something went wrong]_fout bij het negeren van meldingen in het dialoogvenster [!DNL Commerce] Admin. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-47336. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden): 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker ziet _[!UICONTROL Something went wrong]_fout bij het negeren van meldingen in het dialoogvenster [!DNL Commerce] Admin.

<u>Stappen om te reproduceren</u>:

1. Een bulkbewerking uitvoeren (bijvoorbeeld bulkupdate van productkenmerken uit het productraster).
1. De bewerking voltooien (bijvoorbeeld uitvoeren `bin/magento queue:consumer:start product_action_attribute.update`).
1. Vernieuw de [!DNL Commerce] De pagina Admin, breidt de sectie van het admin- bericht uit en klikt op **[!UICONTROL Dismiss All Completed Tasks]** koppeling.

<u>Verwachte resultaten</u>:

De _[!UICONTROL Something went wrong]_De fout zou niet moeten tonen wanneer het ontruimen van de voltooide taken.

<u>Werkelijke resultaten</u>:

De _[!UICONTROL Something went wrong]_Er wordt een fout weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
