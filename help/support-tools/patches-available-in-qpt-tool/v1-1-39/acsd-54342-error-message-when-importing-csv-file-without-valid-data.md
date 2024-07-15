---
title: 'ACSD-54342: Foutbericht bij het importeren van CSV-bestand zonder geldige gegevens'
description: Pas de ACSD-54342-patch toe om het Adobe Commerce-probleem op te lossen waarbij een onjuist foutbericht optreedt bij het importeren van een CSV-bestand zonder geldige gegevens.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 7f443ad8-c4b7-4294-b38f-9861e221bef2
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-54342: Foutbericht bij het importeren van CSV-bestand zonder geldige gegevens

De ACSD-54342-patch verhelpt het probleem waarbij een onjuist foutbericht optreedt bij het importeren van een CSV-bestand zonder geldige gegevens. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.39 wordt geïnstalleerd. De patch-id is ACSD-54342. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een onjuist foutbericht weergegeven wanneer u een CSV-bestand zonder geldige gegevens importeert.

<u> Stappen om </u> te reproduceren:

1. Maak een importbestand met alleen ongeldige gegevens (Voorbeelden: [!DNL SKUs] die niet bestaan, ongeldige adresvelden van klanten of onjuist gevormde e-mailadressen van klanten).
1. Importeer het bestand en selecteer deze optie om de validatiefouten over te slaan.

<u> Verwachte resultaten </u>:

De validatie mislukt met het bericht `There are no valid rows to import` .

<u> Ware resultaten </u>:

De validatie gaat door, maar het importeren mislukt met het bericht `Error in data structure: values are mixed` .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
