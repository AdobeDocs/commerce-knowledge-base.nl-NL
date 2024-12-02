---
title: 'ACSD-47704: Gebundeld product toont de prijs van uitsluitend in voorraad zijnde producten'
description: Pas de ACSD-47704-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een gebundeld product alleen de prijs van in-stock producten weergeeft.
exl-id: 91fbeaf7-4bc2-49b1-a561-c3e63f193eaa
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# ACSD-47704: Gebundeld product toont de prijs van uitsluitend in voorraad zijnde producten

De ACSD-47704-patch verhelpt het probleem waarbij de prijzen van klantensegmenten onjuist tussen klantgroepen worden vastgelegd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 wordt geïnstalleerd. De patch-id is ACSD-47704. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijs van een gebundeld product waarvoor dynamische prijsstelling is ingeschakeld, is onjuist omdat alleen items in voorraad worden opgenomen.

<u> Stappen om </u> te reproduceren:

1. Ga naar het deelvenster Commerce Admin.
1. Ga naar **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]** .
1. Plaats **[UICONROL Dynamische Prijs]** aan **[!UICONTROL Yes]**.
1. Bundle-items:
   * **[!UICONTROL Ship bundle items]** instellen op **[!UICONTROL Together]**
   * Selecteren **[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Selectievakje Markeren is vereist
      * Voeg een eenvoudig product in voorraad toe, bijvoorbeeld Joust Duffle Bag SKU 24-MB01. Voordat u het product gaat toevoegen, noteert u de prijs - $ 34
   * Standaardhoeveelheid: 1
   * Selecteren **[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Selectievakje Markeren is vereist
      * Voeg een eenvoudig product toe dat in voorraad is, anders dan het product dat u eerder hebt toegevoegd, bijvoorbeeld - Strive Shoulder Pack 24-MB04. Voordat u het product gaat toevoegen, noteert u de prijs - $ 32
      * Standaardhoeveelheid: 1
1. Product opslaan.
1. Ga naar de winkel en zoek het product dat u in de vorige stappen hebt gemaakt. Noteer de prijs - $66
(66 = 32 + 34).
Momenteel is de prijs van het bundelproduct gelijk aan de som van de prijzen van de opties.
1. Ga naar het deelvenster Commerce Admin. Ga naar **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** .
1. Zoek een van de eenvoudige producten die als optie aan het bundelproduct eerder zijn toegewezen:
SKU 24-MB01 en een prijs van $34.
1. Wijzig de hoeveelheid in 0.
1. Sla het product op.
1. Ga naar de winkel en zoek het bundelproduct dat u in de vorige stappen hebt gemaakt. Noteer de prijs - $32. Voorheen werd het geprijst bij $66, die de som $34 van SKU 24-MB01 en $32 van SKU 24-MB04 was. Nu het product 24 MB01 uit voorraad is, wordt de bundelprijs weergegeven als $32. Het is de prijs van het andere product, dat een optie in voorraad is.

<u> Verwachte resultaten </u>:

De prijs van bundelproducten waarvoor dynamische prijsstelling is ingeschakeld, wordt consistent berekend, ongeacht of de opties in voorraad of uit voorraad zijn.

<u> Ware resultaten </u>:

De prijs van het bundelproduct waarvoor dynamische prijsstelling is ingeschakeld, is onjuist berekend. Er wordt alleen rekening gehouden met opties die in voorraad zijn, wat resulteert in een lager weergegeven bedrag dan het werkelijke bedrag wanneer een van de opties uit voorraad is.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
