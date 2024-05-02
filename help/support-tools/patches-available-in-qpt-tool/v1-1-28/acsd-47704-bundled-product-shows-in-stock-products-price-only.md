---
title: "ACSD-47704: Gebundeld product toont de prijs van uitsluitend in voorraad zijnde producten"
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

De ACSD-47704-patch verhelpt het probleem waarbij de prijzen van klantensegmenten onjuist tussen klantgroepen worden vastgelegd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 is geïnstalleerd. De patch-id is ACSD-47704. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijs van een gebundeld product waarvoor dynamische prijsstelling is ingeschakeld, is onjuist omdat alleen items in voorraad worden opgenomen.

<u>Stappen om te reproduceren</u>:

1. Ga naar het deelvenster Commerce Admin.
1. Ga naar **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**.
1. Set **[UICONROL Dynamic Price]** tot **[!UICONTROL Yes]**.
1. Bundle-items:
   * Set **[!UICONTROL Ship bundle items]** tot **[!UICONTROL Together]**
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
1. Ga naar de winkel en zoek het product dat u in de vorige stappen hebt gemaakt. Noteer de prijs - $66 (66 = 32 + 34).
Momenteel is de prijs van het bundelproduct gelijk aan de som van de prijzen van de opties.
1. Ga naar het deelvenster Commerce Admin. Ga naar **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**.
1. Vind één van de eenvoudige producten die als optie aan het bundelproduct vroeger worden toegewezen: SKU 24-MB01 en een prijs van $34.
1. Wijzig de hoeveelheid in 0.
1. Sla het product op.
1. Ga naar de winkel en zoek het bundelproduct dat u in de vorige stappen hebt gemaakt. Noteer de prijs - $32. Voorheen werd het geprijst bij $66, die de som $34 van SKU 24-MB01 en $32 van SKU 24-MB04 was. Nu het product 24 MB01 uit voorraad is, wordt de bundelprijs weergegeven als $32. Het is de prijs van het andere product, dat een optie in voorraad is.

<u>Verwachte resultaten</u>:

De prijs van bundelproducten waarvoor dynamische prijsstelling is ingeschakeld, wordt consistent berekend, ongeacht of de opties in voorraad of uit voorraad zijn.

<u>Werkelijke resultaten</u>:

De prijs van het bundelproduct waarvoor dynamische prijsstelling is ingeschakeld, is onjuist berekend. Er wordt alleen rekening gehouden met opties die in voorraad zijn, wat resulteert in een lager weergegeven bedrag dan het werkelijke bedrag wanneer een van de opties uit voorraad is.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
