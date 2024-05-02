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

De ACSD-54342-patch verhelpt het probleem waarbij een onjuist foutbericht optreedt bij het importeren van een CSV-bestand zonder geldige gegevens. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.39 is geïnstalleerd. De patch-id is ACSD-54342. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een onjuist foutbericht weergegeven wanneer u een CSV-bestand zonder geldige gegevens importeert.

<u>Stappen om te reproduceren</u>:

1. Een importbestand maken met alleen ongeldige gegevens (voorbeelden: [!DNL SKUs] die niet bestaan, ongeldige gebieden van het klantenadres, of misvormde klant e-mailadressen).
1. Importeer het bestand en selecteer deze optie om de validatiefouten over te slaan.

<u>Verwachte resultaten</u>:

De validatie mislukt met `There are no valid rows to import` bericht.

<u>Werkelijke resultaten</u>:

De validatie gaat door, maar het importeren mislukt met `Error in data structure: values are mixed` bericht.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
