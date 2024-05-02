---
title: "ACSD-48661: door het bedrijf afgegeven validatie van komma's als scheidingsteken voor kredietlimieten"
description: Pas de ACSD-48661-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het komma-scheidingsteken het opslaan van het bedrijf verhindert vanwege een validatiefout wanneer de limiet van het bedrijfskrediet hoger is dan 999.
exl-id: 85c5a93f-76c5-439b-adcc-511f8473f302
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-48661: door het bedrijf afgegeven validatie van komma&#39;s als scheidingsteken voor kredietlimiet

De ACSD-48661-patch verhelpt het probleem dat wanneer de bedrijfskredietlimiet hoger is dan 999, het komma-scheidingsteken het bedrijf niet kan opslaan als gevolg van een validatiefout. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 is geïnstalleerd. De patch-id is ACSD-4861. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als de kredietlimiet van het bedrijf groter is dan 999, voorkomt het scheidingsteken met komma&#39;s dat het bedrijf opslaat als gevolg van een validatiefout.

<u>Stappen om te reproduceren</u>:

1. Laat de bedrijfseigenschap toe bij **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Een onderneming oprichten en een kredietlimiet toevoegen die groter is dan 999 in het kader van de **[!UICONTROL Company Credit]** tab.
1. Sla het bedrijf op.
1. Bewerk het bedrijf en sla het opnieuw op.

<u>Verwachte resultaten</u>:

U kunt het bedrijf opslaan zonder de kredietlimiet te bepalen. Komma wordt niet ondersteund voor invoervelden voor de bedragen en prijzen.

<u>Werkelijke resultaten</u>:

U kunt het bedrijf niet opslaan vanwege een validatiefout in het dialoogvenster *[!UICONTROL Credit Limit]* veld. Adobe Commerce voegt automatisch komma-scheidingstekens toe voor kredietlimieten, ook al worden de [!UICONTROL Credit Limit] veld accepteert geen komma&#39;s.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
