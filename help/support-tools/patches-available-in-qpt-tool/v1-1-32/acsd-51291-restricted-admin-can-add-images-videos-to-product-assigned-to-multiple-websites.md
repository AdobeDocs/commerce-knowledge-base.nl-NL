---
title: '''ACSD-51291: beperkte beheerders kunnen afbeeldingen/video''s toevoegen aan producten die zijn toegewezen aan meerdere websites'''
description: Pas de ACSD-51291-patch toe om het Adobe Commerce-probleem op te lossen, waarbij beperkte beheerders met toegang tot één website afbeeldingen/video's kunnen toevoegen aan een product dat is toegewezen aan meerdere websites.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: d3cf5009-6b80-4841-95c3-75bb15c9c0a4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# ACSD-51291: beperkte beheerders kunnen afbeeldingen/video&#39;s toevoegen aan producten die zijn toegewezen aan meerdere websites

De ACSD-51291-patch verhelpt het probleem dat een beperkte beheerder met toegang tot één website afbeeldingen/video&#39;s kan toevoegen aan een product dat is toegewezen aan meerdere websites. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 is geïnstalleerd. De patch-id is ACSD-51291. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een beperkte beheerder met toegang tot één website kan afbeeldingen/video&#39;s toevoegen aan een product dat is toegewezen aan meerdere websites.

<u>Stappen om te reproduceren</u>

1. Meld u aan als beheerder.
1. Maak een tweede website, sla deze op en sla de weergave op.
1. Maak een tweede beheerdersrol met alleen bronnen voor de tweede website, de tweede winkel en de opslagweergave.
1. Creeer tweede admin, en wijs het aan de nieuwe beperkte admin rol toe.
1. Maak een nieuw product en wijs dit toe aan zowel de standaardwebsite als de nieuwe website.
1. Log uit van het hoofdbeheerprofiel.
1. Meld u aan als de nieuwe beperkte beheerder.
1. Bewerk het gemaakte product dat aan beide websites is toegewezen.
1. Open de **[!UICONTROL Images and Videos]** tab.

<u>Verwachte resultaten</u>:

* Het volgende bericht wordt weergegeven:

  *Beperkte beheerders mogen alleen handelingen uitvoeren met afbeeldingen of video&#39;s als de beheerder rechten heeft op alle websites waaraan het product is toegewezen.*

* De **[!UICONTROL Add Video]** is niet actief.

<u>Werkelijke resultaten</u>:

De beperkte beheerder kan afbeeldingen en video&#39;s toevoegen, zelfs als het product is toegewezen aan een website waartoe het geen toegang heeft.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
