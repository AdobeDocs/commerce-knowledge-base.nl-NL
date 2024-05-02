---
title: 'ACSD-51471: Admin-gebruiker kan geplande update voor gebundeld product niet opslaan'
description: Pas de ACSD-51471-patch toe om het Adobe Commerce-probleem op te lossen waarbij een beheerder geen geplande update kan opslaan voor een gebundeld product dat een eenvoudig product met een geplande update gebruikt.
exl-id: 7d80aef0-8505-4491-bde3-5b1a30b840f6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-51471: Admin-gebruiker kan geplande update voor gebundeld product niet opslaan

De ACSD-51471-patch verhelpt het probleem waarbij een beheerder geen geplande update kan opslaan voor een gebundeld product dat een eenvoudig product met een geplande update gebruikt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-51471. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruikers kunnen geen geplande update opslaan voor een gebundeld product dat een eenvoudig product gebruikt waarvoor zelf een geplande update beschikbaar is.

<u>Stappen om te reproduceren</u>:

1. Maak een eenvoudig product.
1. Voeg een geplande update voor het eenvoudige product toe met alleen de opdracht *Begindatum* en nee *Einddatum*.
1. Nadat de update is toegepast, wijzigt u de SKU van het product.
1. Maak een gebundeld product en voeg het eenvoudige product dat in Stap 1 is gemaakt toe als een onderliggend product.
1. Maak een geplande update voor het gebundelde product om het gebundelde product mogelijk te maken. Beide opgeven *Begindatum* en *Einddatum* voor de geplande update.
1. Sla de geplande update op.

<u>Verwachte resultaten</u>:

De geplande update is opgeslagen.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op wanneer u de geplande update opslaat: *Het aangevraagde product bestaat niet. Controleer het product en probeer het opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
