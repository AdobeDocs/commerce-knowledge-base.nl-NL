---
title: 'ACSD-49706: standaardwaarde wordt opgeslagen voor kenmerk van visueel staal wanneer geen waarde is geselecteerd'
description: Pas de ACSD-49706-patch toe om het Adobe Commerce-probleem op te lossen waarbij een standaardwaarde wordt opgeslagen voor een visueel staalkenmerk wanneer geen waarde is geselecteerd.
exl-id: fe6071df-f2a4-443a-acfa-67f3d253c5e4
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-49706: standaardwaarde opgeslagen voor kenmerk van visueel staal wanneer geen waarde is geselecteerd

De ACSD-49706-patch verhelpt het probleem waarbij een standaardwaarde wordt opgeslagen voor een visueel staalkenmerk wanneer geen waarde is geselecteerd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-49706. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als er geen waarde is geselecteerd, wordt een standaardwaarde voor een visueel staalkenmerk opgeslagen.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Klik op **[!UICONTROL Add New Attribute]**.
1. Vul de velden in.

   * Kies bijvoorbeeld invoertype *[!UICONTROL Visual Swatch]* en voegt u meerdere opties toe (zoals *Rood*, *Groen*). Kies een van deze opties als standaardopties.
   * Klik op **[!UICONTROL Save Attribute]**.

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Bewerk de *[!UICONTROL Default]* kenmerkset.
1. Verplaatsen *[!UICONTROL New Attribute]* uit de kolom *[!UICONTROL Unassigned Attributes]* aan de *[!UICONTROL Product Details]* in de middelste kolom.

   * Klik op **[!UICONTROL Save]**.

1. Een nieuw product maken met de *[!UICONTROL Default]* kenmerkset.

   * Laat de *[!UICONTROL New Attribute]* leeg maken en opslaan.

1. Als de waarde eenmaal is opgeslagen, wordt deze weergegeven in *[!UICONTROL New Attribute]*.

<u>Verwachte resultaten</u>:

Er is geen waarde toegewezen aan *[!UICONTROL New Attribute]* standaard.

<u>Werkelijke resultaten</u>:

Bij het opslaan van een product wordt een standaardwaarde op het kenmerk toegepast.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
