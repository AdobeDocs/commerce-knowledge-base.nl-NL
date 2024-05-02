---
title: 'ACSD-46520: Onjuiste orderstatus bij teruggaaf met gebruik van winkelcredits'
description: Dit artikel biedt een oplossing voor het probleem waarbij gebruikers een onjuiste orderstatus krijgen wanneer ze deze terugbetalen met gebruik van winkelcredits.
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520: onjuiste orderstatus bij teruggave via winkelcredits

De ACSD-46520-patch lost het probleem op waarbij gebruikers een onjuiste orderstatus krijgen wanneer ze deze terugbetalen met gebruik van opslagkredieten. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 is geïnstalleerd. De patch-id is ACSD-46520. De kwestie is opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 en 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers krijgen een onjuiste status van de bestelling wanneer ze deze terugbetalen met gebruik van winkelcredits.

<u>Stappen om te reproduceren</u>:

1. Maak een klantenaccount op de winkel en meld u aan.
1. Wijs opslagkredieten toe aan de klant vanuit de beheerder. De winkelkredieten moeten de hele bestelling dekken.
1. Plaats een bestelling met de winkelcredits.
1. Factuur de bestelling.
1. Maak een creditnota om het volledige bedrag van de bestelling terug te betalen.
Selecteer de **[!UICONTROL Refund to store credit]** selectievakje.
1. Controleer de orderstatus.

<u>Verwachte resultaten</u>:

De orderstatus is *Gesloten*.

<u>Werkelijke resultaten</u>:

De orderstatus is *Voltooid*, wat niet de juiste status is.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of [!DNL Magento Open Source] ter plaatse: [Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding voor het gereedschap Kwaliteitspatches.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de handleiding voor het gereedschap Kwaliteitspatches.
