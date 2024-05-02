---
title: "ACSD-56280: Aankopen van cadeauregisters zijn niet voltooid"
description: Pas de ACSD-56280-patch toe om het Adobe Commerce-probleem op te lossen waarbij de aankopen van het cadeauregister niet zijn voltooid
feature: Checkout
role: Admin
exl-id: 8e78ea1d-bd55-49d7-9d74-748b8f90e28c
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-56280: aankopen van cadeauregisters worden niet voltooid

De ACSD-56280-patch verhelpt het probleem waarbij de aankopen van het cadeauregister niet zijn voltooid. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 is geïnstalleerd. De patch-id is ACSD-56280. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aankopen van het cadeauregister worden niet voltooid.

<u>Stappen om te reproduceren</u>:

1. Meld u aan als klant en voeg een **[!UICONTROL product]** aan cadeauregister.
1. Deel de koppeling voor het cadeauregister.
1. Open de koppeling voor het cadeauregister in een andere browser/incognito-venster.
1. Voeg de hoeveelheid toe en voeg de items toe aan het winkelwagentje.
1. Ga naar de **[!UICONTROL Checkout Page]**, selecteert u **[!UICONTROL shipping method]**(Aangezien het verzendadres al is geselecteerd, opgegeven door de registrant).
1. Selecteer de betalingsmethode.
1. Klik op de knop Plaatsvolgorde.

<u>Verwachte resultaten</u>:

De volgorde moet worden geplaatst.

<u>Werkelijke resultaten</u>:

De volgorde wordt niet geplaatst en de weergegeven fout is: `Call to a member function getUpdatedQty() on null`.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
