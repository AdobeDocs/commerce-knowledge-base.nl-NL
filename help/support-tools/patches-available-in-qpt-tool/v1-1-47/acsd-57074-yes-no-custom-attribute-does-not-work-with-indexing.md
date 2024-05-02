---
title: "ACSD-57074: *Yes/No* custom attribute with ` price_*` prefix in ` attribute_code` attribute does not work with indexing"
description: Pas het ACSD-57074 flard toe om de kwestie van Adobe Commerce te bevestigen waar het *Yes/No* douanekenmerk met ` price_* ` prefix in ` attribuut_code ` niet met indexeren werkt.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: c620722f-a66d-4cae-9614-becec589a78c
source-git-commit: 4197f2a8f3d4775d3459b17bd92fa51a54ff9607
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-57074: *Ja/Nee* aangepast kenmerk met `price_*` prefix in `attribute_code` kenmerk werkt niet met indexeren

De ACSD-57074-patch verhelpt het probleem waarbij de *Ja/Nee* aangepast kenmerk met `price_*` in het dialoogvenster `attribute_code` kenmerk werkt niet met indexeren. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.47 is geïnstalleerd. De patch-id is ACSD-57074. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De *Ja/Nee* aangepast kenmerk met `price_*` in het dialoogvenster `attribute_code` kenmerk werkt niet met indexeren.

<u>Stappen om te reproduceren</u>:

1. Maak een aangepast productkenmerk met de volgende opties:
   * *[!UICONTROL Catalog Input Type]*: *Ja/Nee*
   * *[!UICONTROL Scope]*: *Winkelweergave*
   * *[!UICONTROL Use in Search]*: *Ja*
1. Wijs het kenmerk toe aan de standaardkenmerkset.
1. Maak een product met het kenmerk dat we hebben gemaakt.
1. Wijs het product dat we zojuist hebben gemaakt toe aan een categorie.
1. Voer de volledige redex uit.

<u>Verwachte resultaten</u>:

Het product wordt weergegeven in de toegewezen categorie.

<u>Werkelijke resultaten</u>:

Het product staat niet op de voorpagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
