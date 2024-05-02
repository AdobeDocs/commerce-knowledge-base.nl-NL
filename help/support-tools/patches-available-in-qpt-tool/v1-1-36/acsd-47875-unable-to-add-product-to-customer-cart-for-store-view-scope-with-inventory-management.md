---
title: "ACSD-47875: kan geen product aan winkelwagentje toevoegen voor weergavebereik met voorraadbeheer"
description: Pas de ACSD-47875-patch toe om het Adobe Commerce-probleem op te lossen waarbij een product niet vanuit Admin aan een klantenkar kan worden toegevoegd voor een bepaald weergavebereik in de winkel met voorraadbeheer.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: fa5ecd65-704f-49bd-b3cc-3d60ff7e1dce
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-47875: kan geen product aan winkelwagentje toevoegen voor weergavebereik met voorraadbeheer

De ACSD-47875-patch verhelpt het probleem dat een product niet kan worden toegevoegd aan een klankkaart van de beheerder voor een bepaald weergavebereik van de winkel met voorraadbeheer. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.36 is geïnstalleerd. De patch-id is ACSD-47875. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruikers kunnen een product niet aan een klantenkar toevoegen met de **[!UICONTROL Manage Shopping Cart]** in Admin voor een bepaald gebied van de archiefmening met geïnstalleerd MSI.

<u>Vereisten</u>:

[!DNL Adobe Commerce Inventory Management (MSI)] modules worden geïnstalleerd en ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Maak een website, een winkel en een winkelweergave.
1. Een andere bron maken dan *Standaard*.
1. Maak een nieuwe voorraad en wijs deze toe aan de nieuwe website en de nieuwe bron.
1. Maak een nieuwe klant voor de nieuwe website.
1. Alleen een product aan de nieuwe website toewijzen; toewijzing van de standaardwebsite ongedaan maken.

   * Wijs de nieuwe bron toe en plaats Aantal *boven 0* voor de nieuwe bron en *0* voor de standaardbron.

1. Ga naar de **[!UICONTROL Customer Edit]** in Admin. Klik op **[!UICONTROL Manage Shopping Cart]**.
1. Wijzig het bereik van de winkelweergave in de nieuwe winkelweergave.
1. Ga naar de **[!UICONTROL Products]** en zoek naar het product.
1. Selecteer het product en klik op **[!UICONTROL Add selections to my cart]**.

<u>Verwachte resultaten</u>:

Het product wordt toegevoegd aan het winkelwagentje.

<u>Werkelijke resultaten</u>:

* De volgende fout wordt gegenereerd: *Het product dat u wilt toevoegen, is niet beschikbaar.*
* Het product wordt niet toegevoegd aan het winkelwagentje.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
