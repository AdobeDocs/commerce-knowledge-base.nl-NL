---
title: "ACSD-52398: Gevraagde hoeveelheid is niet beschikbaar wanneer wordt geprobeerd de hoeveelheid gebundeld product bij te werken"
description: Pas de ACSD-52398-patch toe om het Adobe Commerce-probleem op te lossen wanneer de gevraagde hoeveelheid niet beschikbaar is wanneer wordt geprobeerd de hoeveelheid van een gebundeld product in het winkelwagentje bij te werken.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 7b7f06ac-7913-4603-992a-a5620045d828
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-52398: Gevraagde hoeveelheid is niet beschikbaar wanneer wordt geprobeerd de hoeveelheid gebundeld product bij te werken

De ACSD-52398-patch verhelpt het probleem dat de gevraagde hoeveelheid niet beschikbaar is wanneer wordt geprobeerd de hoeveelheid van een gebundeld product in het winkelwagentje bij te werken. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-52398. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gevraagde hoeveelheid is niet beschikbaar wanneer wordt geprobeerd de hoeveelheid van een gebundeld product in het winkelwagentje bij te werken.

<u>Stappen om te reproduceren</u>:

1. Twee eenvoudige producten met hoeveelheid maken *1* en *10*.
1. Maak een gebundeld product met de eenvoudige producten.
1. Voeg het gebundelde product aan de kar toe.
1. Bewerk het product en probeer het aantal bij te werken naar *3* voor de optie *10* objecten zijn beschikbaar.

<u>Verwachte resultaten</u>:

Er is geen fout. Aantal is bijgewerkt omdat er *10* posten in voorraad voor deze optie.

<u>Werkelijke resultaten</u>:

De volgende fout wordt gegenereerd: *De gevraagde hoeveelheid is niet beschikbaar*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
