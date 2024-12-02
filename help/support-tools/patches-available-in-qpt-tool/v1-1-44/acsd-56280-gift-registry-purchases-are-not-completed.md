---
title: 'ACSD-56280: aankopen van cadeauregisters worden niet voltooid'
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

De ACSD-56280-patch verhelpt het probleem waarbij de aankopen van het cadeauregister niet zijn voltooid. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 wordt geïnstalleerd. De patch-id is ACSD-56280. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aankopen van het cadeauregister worden niet voltooid.

<u> Stappen om </u> te reproduceren:

1. Meld u aan als klant en voeg een **[!UICONTROL product]** toe aan een cadeauregister.
1. Deel de koppeling voor het cadeauregister.
1. Open de koppeling voor het cadeauregister in een andere browser/incognito-venster.
1. Voeg de hoeveelheid toe en voeg de items toe aan het winkelwagentje.
1. Ga naar **[!UICONTROL Checkout Page]** en selecteer **[!UICONTROL shipping method]** (Aangezien het verzendadres al is geselecteerd, opgegeven door de registrant).
1. Selecteer de betalingsmethode.
1. Klik op de knop Plaatsvolgorde.

<u> Verwachte resultaten </u>:

De volgorde moet worden geplaatst.

<u> Ware resultaten </u>:

De volgorde wordt niet geplaatst en de weergegeven fout is: `Call to a member function getUpdatedQty() on null` .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
