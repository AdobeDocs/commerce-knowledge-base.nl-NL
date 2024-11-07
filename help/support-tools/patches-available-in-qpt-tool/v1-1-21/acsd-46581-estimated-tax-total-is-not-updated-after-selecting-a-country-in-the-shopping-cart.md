---
title: "ACSD-46581: Het geraamde belastingtotaal wordt niet bijgewerkt na selectie van een land in het winkelwagentje."
description: Pas de ACSD-46581-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het belastingtarief niet wordt aangepast nadat het land in het winkelwagentje is verschoven.
exl-id: 17334f7b-e5a2-4091-8196-eff80875c003
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-46581: Het geraamde belastingtotaal wordt niet bijgewerkt na selectie van een land in het winkelwagentje

Deze ACSD-46581-patch lost het probleem op dat het belastingtarief niet wordt aangepast nadat het land in het winkelwagentje is verschoven. Het wordt pas bijgewerkt nadat u de verzendmethode hebt geselecteerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 wordt geïnstalleerd. De patch-id is ACSD-46581. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het belastingtarief wordt niet bijgewerkt nadat het land in het winkelwagentje is veranderd.

<u> Stappen om </u> te reproduceren:

1. Ga in Adobe Commerce Admin naar **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]** .
1. Creeer een nieuw belastingtarief voor **[!UICONTROL Country]** = _Verenigde Staten_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8.25_.
1. Creeer een nieuw belastingtarief voor **[!UICONTROL Country]** = _India_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Maak een belastingregel met zowel belastingtarieven voor de VS als voor India.
1. Ga naar **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** en laat meer dan één het verschepen methode toe (_Vlakke Tarief_ en _Vrij Verschepend_ bijvoorbeeld).
1. Maak een eenvoudig product met de belastingklasse **[!UICONTROL Taxable Goods]** .
1. Voeg een product toe aan de winkelwagentje.
1. Open het winkelwagentje en controleer het belastingbedrag.
1. De standaardbelastinginstellingen voor de Verenigde Staten worden toegepast en de belasting wordt berekend op basis van een tarief van 8,25%.
1. Ga van land naar India.

<u> Verwachte resultaten </u>:

Het belastingbedrag is veranderd in 10% bij de overstap van het land naar India.

<u> Ware resultaten </u>:

Het belastingbedrag blijft hetzelfde in het totale gedeelte van het winkelwagentje.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
