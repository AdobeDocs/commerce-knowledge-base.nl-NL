---
title: '"ACSD-54776: niet gecontroleerd [!UICONTROL Use Default Value] en niet-standaardwaarden voor productvelden worden niet opgeslagen voor de tweede website-, winkel- en winkelweergave.'''
description: Pas de ACSD-54776-patch toe om het Adobe Commerce-probleem op te lossen waarbij het niet is ingeschakeld [!UICONTROL Use Default Value] en niet-standaardwaarden voor productvelden worden niet opgeslagen voor de tweede website-, winkel- en winkelweergave.
feature: Products
role: Admin, Developer
exl-id: 5bdad804-8d7b-48b4-ba3b-c2d5387ef55e
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-54776: Niet ingeschakeld *[!UICONTROL Use Default Value]* en niet-standaardwaarden voor productvelden worden niet opgeslagen

>[!NOTE]
>
>Deze patch vervangt de [ACSD-51984](/help/support-tools/patches-available-in-qpt-tool/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) die in QPT 1.1.35 wordt vrijgegeven.

De ACSD-54776-patch verhelpt het probleem waarbij de niet-aangevinkte **[!UICONTROL Use Default Value]** en niet-standaardwaarden voor productvelden worden niet opgeslagen voor de tweede website-, winkel- en winkelweergave. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 is geïnstalleerd. De patch-id is ACSD-54776. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p4, 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Uitgeschakeld *[!UICONTROL Use Default Value]* en niet-standaardwaarden voor productvelden worden niet opgeslagen voor de tweede website-, winkel- en winkelweergave.

<u>Stappen om te reproduceren</u>:

1. Naar de achtergrond gaan en naar **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** en maak een nieuwe website, winkel en winkelweergave.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, maakt u een eenvoudig product en slaat u dit op en wijst u het product via de **[!UICONTROL Product in Websites]**.
1. Verander het werkingsgebied in de pas gecreëerde opslagmening van stap 2.
1. Ga naar **[!UICONTROL Search Engine Optimization]** en deselecteer de **[!UICONTROL Use Default Value]** selectievakjes voor [!UICONTROL Meta Title], [!UICONTROL Meta Keywords], en [!UICONTROL Meta Description].
1. Maak de tekst uit de velden schoon: *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* en *[!UICONTROL Meta Description]* en klik op **[!UICONTROL Save]**.
1. Ga naar **[!UICONTROL Search Engine Optimization]** opnieuw.

<u>Verwachte resultaten</u>

De waarden voor de velden en selectievakjes worden opgeslagen.

<u>Werkelijke resultaten</u>

De waarden voor de velden en selectievakjes worden niet opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
