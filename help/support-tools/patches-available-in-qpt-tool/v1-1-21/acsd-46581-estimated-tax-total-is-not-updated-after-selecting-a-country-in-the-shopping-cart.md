---
title: "ACSD-46581: Het geraamde belastingtotaal wordt niet bijgewerkt na selectie van een land in het winkelwagentje."
description: Pas de ACSD-46581-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het belastingtarief niet wordt aangepast nadat het land in het winkelwagentje is verschoven.
exl-id: 17334f7b-e5a2-4091-8196-eff80875c003
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-46581: Het geraamde belastingtotaal wordt niet bijgewerkt na selectie van een land in het winkelwagentje

Deze ACSD-46581-patch lost het probleem op dat het belastingtarief niet wordt aangepast nadat het land in het winkelwagentje is verschoven. Het wordt pas bijgewerkt nadat u de verzendmethode hebt geselecteerd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 is geïnstalleerd. De patch-id is ACSD-46581. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met Adobe Commerce-versies:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het belastingtarief wordt niet bijgewerkt nadat het land in het winkelwagentje is veranderd.

<u>Stappen om te reproduceren</u>:

1. Ga in Adobe Commerce Admin naar **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. Een nieuw BTW-tarief maken voor **[!UICONTROL Country]** = _Verenigde Staten_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8,25_.
1. Een nieuw BTW-tarief maken voor **[!UICONTROL Country]** = _India_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Maak een belastingregel met zowel belastingtarieven voor de VS als voor India.
1. Ga naar **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** en schakel meerdere verzendmethoden in (_Platte snelheid_ en _Gratis verzending_ bijvoorbeeld).
1. Een eenvoudig product maken met de **[!UICONTROL Taxable Goods]** belastingklasse.
1. Voeg een product toe aan de winkelwagentje.
1. Open het winkelwagentje en controleer het belastingbedrag.
1. De standaardbelastinginstellingen voor de Verenigde Staten worden toegepast en de belasting wordt berekend op basis van een tarief van 8,25%.
1. Ga van land naar India.

<u>Verwachte resultaten</u>:

Het belastingbedrag is veranderd in 10% bij de overstap van het land naar India.

<u>Werkelijke resultaten</u>:

Het belastingbedrag blijft hetzelfde in het totale gedeelte van het winkelwagentje.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere pleisters beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
