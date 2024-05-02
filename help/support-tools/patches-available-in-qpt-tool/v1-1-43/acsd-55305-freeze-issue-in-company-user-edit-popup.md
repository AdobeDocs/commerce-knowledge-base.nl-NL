---
title: 'ACSD-55305: Pop-up bevriest tijdens bewerking door bedrijfsgebruiker in [!UICONTROL My Account]'
description: Pas de ACSD-55305-patch toe om het Adobe Commerce-probleem op te lossen, waarbij [!UICONTROL Edit Company User] popup [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] pagina loopt vast met een lader op het scherm.
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305: Pop-up bevriest tijdens bewerking door bedrijfsgebruiker in [!UICONTROL My Account]

De ACSD-55305-patch verhelpt het probleem waarbij  [!UICONTROL Edit Company User] popup [!UICONTROL My Account]> [!UICONTROL Company Structure] pagina loopt vast met een lader op het scherm. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 is geïnstalleerd. De patch-id is ACSD-55305. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een fout op bij het gebruik van de *[!UICONTROL Edit Company User]* popup *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* pagina vastloopt terwijl een lader op het scherm wordt weergegeven.

<u>Stappen om te reproduceren</u>:

1. Een B2B-bedrijf oprichten.
1. Maak een kenmerk met meerdere selecties voor klanten.
1. Wijs een waarde aan het pas gecreëerde attribuut voor bedrijfbeheerder toe.
1. Meld u aan als bedrijfsbeheerder.
1. Ga naar de [!UICONTROL account dashboard] en navigeer naar de **[!UICONTROL Company Structure]**.
1. Selecteer de gebruiker.
1. Klikken op **[!UICONTROL Edit Selected]**.

<u>Verwachte resultaten</u>:

Het pop-upvenster van het formulier wordt correct weergegeven en biedt de mogelijkheid om bedrijfsgegevens te bewerken.

<u>Werkelijke resultaten</u>:

Het pop-upvenster van het formulier wordt weergegeven zonder mogelijkheid om te bewerken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
