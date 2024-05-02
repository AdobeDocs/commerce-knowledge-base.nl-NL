---
title: 'ACSD-54026: Onjuist foutbericht voor updateCompanyRole GraphQL-verzoek'
description: Pas de ACSD-54026-patch toe om het Adobe Commerce-probleem op te lossen wanneer er een onjuist foutbericht is voor een updateCompanyRole GraphQL-verzoek voor een niet-geautoriseerde gebruiker.
feature: Roles/Permissions
role: Admin, Developer
exl-id: c18a8815-975a-499d-a372-8635d89aa673
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-54026: Onjuist foutbericht voor `updateCompanyRole` GraphQL-verzoek

De ACSD-54026-patch verhelpt het probleem bij een onjuist foutbericht voor een `updateCompanyRole` GraphQL-verzoek voor een niet-gemachtigde gebruiker. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.39 is geïnstalleerd. De patch-id is ACSD-54026. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een onjuist foutbericht ophalen voor een `updateCompanyRole` GraphQL-verzoek voor een niet-gemachtigde gebruiker.

<u>Stappen om te reproduceren</u>:

1. B2B-bedrijf inschakelen in configuratie.
1. Maak een bedrijf.
1. Een `updateCompanyRole` GraphQL-aanvraag zonder een token voor toonder door te geven of met een ongeldige token voor toonder.
1. Bekijk het foutbericht in het GraphQL-antwoord.

<u>Verwachte resultaten</u>:

U krijgt het volgende foutbericht: *De huidige klant is niet geautoriseerd.*

<u>Werkelijke resultaten</u>:

U krijgt het volgende foutbericht: *De klant is geen gebruiker van het bedrijf.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
