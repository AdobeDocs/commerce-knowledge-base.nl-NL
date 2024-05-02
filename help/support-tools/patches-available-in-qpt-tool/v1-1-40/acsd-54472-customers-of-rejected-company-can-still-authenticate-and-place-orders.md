---
title: 'ACSD-54472: Klanten van een afgewezen bedrijf kunnen nog steeds worden geverifieerd'
description: Pas de ACSD-54472-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de klanten van een afgewezen bedrijf nog steeds kunnen verifiëren en klanten van een geblokkeerd en afgewezen bedrijf nog steeds orders kunnen plaatsen.
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472: klanten van een afgewezen bedrijf kunnen nog steeds verifiëren

De ACSD-54472-patch verhelpt het probleem dat klanten van een afgewezen bedrijf nog steeds kunnen verifiëren en dat klanten van een geblokkeerd en afgewezen bedrijf nog steeds orders kunnen plaatsen. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 is geïnstalleerd. De patch-id is ACSD-54472. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De klanten van een verworpen bedrijf kunnen nog voor authentiek verklaren, en de klanten van een geblokkeerd en verworpen bedrijf kunnen nog orden plaatsen.

<u>Stappen om te reproduceren</u>:

1. Maak een bedrijf.
1. Producten aan het winkelwagentje toevoegen via [!DNL GraphQL].
1. Wijzig de bedrijfsstatus in *Geblokkeerd*.
1. Een [!DNL GraphQL] verzoek om de bestelling te plaatsen en een onderhandelbaar aanhalingsteken te maken.
1. Wijzig de bedrijfsstatus in *Geweigerd*.
1. Een [!DNL GraphQL] verzoek om de token van de gebruikersvergunning van het bedrijf te verkrijgen.
1. Klantstatus instellen op *Inactief*.
1. Een [!DNL GraphQL] verzoek om de token van de gebruikersvergunning van het bedrijf te verkrijgen.

<u>Verwachte resultaten</u>:

* De volgorde en het verhandelbare aanhalingsteken worden niet door de gebruiker van de *Geblokkeerd* bedrijf.
* De machtigingstoken wordt niet opgehaald voor de gebruiker van de *Geweigerd* bedrijf.
* Token voor autorisatie wordt niet opgehaald voor de *Inactief* klant.

<u>Werkelijke resultaten</u>:

* De opdracht Volgorde en verhandelbare aanhalingstekens worden geplaatst door de gebruiker van de *Geblokkeerd* bedrijf.
* Token voor autorisatie wordt opgehaald voor de gebruiker van de *Geweigerd* bedrijf.
* Token voor autorisatie wordt opgehaald voor de *Inactief* klant.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
