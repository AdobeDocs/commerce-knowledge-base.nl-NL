---
title: '"ACSD-49835: [!UICONTROL Use Default Value] selectievakje is niet opgeslagen'''
description: Pas de ACSD-49835-patch toe om het Adobe Commerce-probleem op te lossen waarbij de [!UICONTROL Use Default Value] het selectievakje wordt niet correct opgeslagen op archiefniveau voor een kenmerk voor meerdere selecties.
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835: [!UICONTROL Use Default Value] selectievakje is niet opgeslagen

De ACSD-49835-patch verhelpt het probleem waarbij de [!UICONTROL Use Default Value] het selectievakje wordt niet correct opgeslagen op archiefniveau voor een kenmerk voor meerdere selecties. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-49835. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De [!UICONTROL Use Default Value] het selectievakje wordt niet correct opgeslagen op archiefniveau voor een kenmerk voor meerdere selecties.

<u>Stappen om te reproduceren</u>:

1. Een **[!UICONTROL Multiple-select Attribute]** in **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** en voeg het toe aan een kenmerkset.
1. Ga naar een **[!UICONTROL Product]** en opslaan **[!UICONTROL Values]** in **[!UICONTROL All Store Views (Default Scope)]**.
1. Naar een specifieke **[!UICONTROL Store View Scope]** en sla het product op.
1. Ga naar **[!UICONTROL Store View Scope]** en de **[!UICONTROL Use Default Value]** selectievakje.

<u>Verwachte resultaten</u>:

Kenmerkwaarden voor meerdere selecties worden op de juiste wijze opgeslagen bij het controleren van de opties [!UICONTROL Use Default Value] Selectievakje in het dialoogvenster [!UICONTROL Store View Scope].

<u>Werkelijke resultaten</u>:

Meerdere geselecteerde kenmerkwaarden worden niet correct opgeslagen bij het controleren van de [!UICONTROL Use Default Value] Selectievakje in het dialoogvenster [!UICONTROL Store View Scope].

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
