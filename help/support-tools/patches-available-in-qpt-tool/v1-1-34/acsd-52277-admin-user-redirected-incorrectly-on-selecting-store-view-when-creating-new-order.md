---
title: 'ACSD-52277: Admin-gebruiker is onjuist omgeleid bij het selecteren van de winkelweergave bij het maken van een nieuwe bestelling.'
description: Pas de ACSD-52277-patch toe om het Adobe Commerce-probleem op te lossen waarbij een beheerder niet correct wordt omgeleid nadat hij de winkelweergave heeft geselecteerd bij het maken van een nieuwe bestelling in Admin.
exl-id: 6f0b86ae-f6f1-44cf-aef5-64def5f14824
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-52277: Admin-gebruiker wordt onjuist omgeleid bij het selecteren van de winkelweergave bij het maken van een nieuwe bestelling

De ACSD-52277-patch verhelpt het probleem dat een beheerder niet correct wordt omgeleid nadat hij de winkelweergave heeft geselecteerd bij het maken van een nieuwe bestelling in Admin. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 is geïnstalleerd. De patch-id is ACSD-52277. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4, 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een beheerder wordt niet correct omgeleid nadat hij tijdens het maken van een nieuwe bestelling de winkelweergave heeft geselecteerd.

<u>Stappen om te reproduceren</u>

1. Installeer een schone instantie.
1. Maak een product.
1. Maak een extra website, één winkel en twee winkelweergaven.
1. Een bestelling maken via Beheer door *winkelweergave 1*.

<u>Verwachte resultaten</u>:

De gebruiker wordt omgeleid aan de ordepagina.

<u>Werkelijke resultaten</u>:

Nadat u de winkelweergave hebt geselecteerd, wordt de gebruiker niet omgeleid naar de bestelpagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
