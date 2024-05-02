---
title: 'ACSD-46674: aangepaste opties van afbeeldingstype weergegeven als HTML in e-mails van klanten'
description: Pas de ACSD-46674-patch toe om het Adobe Commerce-probleem op te lossen, waarbij aangepaste opties voor afbeeldingstypen als HTML worden weergegeven in e-mails van klanten.
exl-id: b4941dd0-bb3a-4805-9631-1d256a92f461
feature: Communications, Personalization
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-46674: aangepaste opties voor afbeeldingstype weergegeven als HTML in e-mails van klanten

De ACSD-46674-patch verhelpt het probleem waarbij de aangepaste opties van een afbeeldingstype als HTML worden weergegeven in e-mails van de klant. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 is geïnstalleerd. De patch-id is ACSD-46674. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aangepaste opties van een afbeeldingstype worden als HTML weergegeven in e-mails van klanten.

<u>Stappen om te reproduceren</u>:

1. Maak een product met een aangepaste optie.
   * Type optie: *Bestand*
   * Compatibele bestandsextensies: *png, jpg, gif*
   * Vereist: *Ja*
1. Plaats een bestelling voor dit product met een afbeelding die als een aangepaste optie is geüpload.
1. Maak een factuur voor de bestelling die u in stap 2 maakt.
1. Maak een creditmemo.
1. Controleer alle bevestigingse-mails.

<u>Verwachte resultaten</u>:

De geüploade afbeelding wordt weergegeven in de bevestigingsberichten.

<u>Werkelijke resultaten</u>:

De bevestigingse-mails bevatten de normale HTML-code in plaats van de aangepaste optieafbeelding van het product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tools] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in [!DNL QPT], zie [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
