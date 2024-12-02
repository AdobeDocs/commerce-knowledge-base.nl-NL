---
title: 'ACSD-46674: aangepaste opties voor afbeeldingstype weergegeven als HTML in e-mails van klanten'
description: Pas de ACSD-46674-patch toe om het Adobe Commerce-probleem op te lossen, waarbij aangepaste opties voor afbeeldingstypen als HTML worden weergegeven in e-mails van klanten.
exl-id: b4941dd0-bb3a-4805-9631-1d256a92f461
feature: Communications, Personalization
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-46674: aangepaste opties voor afbeeldingstype weergegeven als HTML in e-mails van klanten

De ACSD-46674-patch verhelpt het probleem waarbij de aangepaste opties van een afbeeldingstype als HTML worden weergegeven in e-mails van de klant. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 wordt geïnstalleerd. De patch-id is ACSD-46674. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aangepaste opties van een afbeeldingstype worden als HTML weergegeven in e-mails van klanten.

<u> Stappen om </u> te reproduceren:

1. Maak een product met een aangepaste optie.
   * Het type van optie: *Dossier*
   * Compatibele dossieruitbreidingen: *png, jpg, gif*
   * Vereist: *ja*
1. Plaats een bestelling voor dit product met een afbeelding die als een aangepaste optie is geüpload.
1. Maak een factuur voor de bestelling die u in stap 2 maakt.
1. Maak een creditmemo.
1. Controleer alle bevestigingse-mails.

<u> Verwachte resultaten </u>:

De geüploade afbeelding wordt weergegeven in de bevestigingsberichten.

<u> Ware resultaten </u>:

De bevestigingse-mails bevatten de normale HTML-code in plaats van de aangepaste optieafbeelding van het product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tools]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Meer informatie over andere patches die beschikbaar zijn in [!DNL QPT] vindt u in [[!DNL Quality Patches Tool] : Zoeken naar patches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] -handleiding.
