---
title: "ACSD-57337: Admin-gebruiker met toegangsbeperkingen kan alle bedrijven bekijken in het *Companies*-netwerk"
description: Pas de ACSD-57337-patch toe om het Adobe Commerce-probleem op te lossen waarbij een beheerder met toegangsbeperkingen voor specifieke websites bedrijven kan bekijken vanaf alle websites in het *Companies*-raster.
feature: Companies, B2B, Configuration
role: Admin, Developer
source-git-commit: a02c80006f1c8a434fe17322f0c6cee25f086396
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-57337: Admin-gebruiker met toegangsbeperkingen kan alle bedrijven in de *Bedrijven* raster

De ACSD-57337-patch verhelpt het probleem dat een beheerder met toegangsbeperkingen voor specifieke websites bedrijven kan bekijken van alle websites in de *Bedrijven* raster. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 is geïnstalleerd. De patch-id is ACSD-57337. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een beheerder die toegangsbeperkingen heeft voor specifieke websites, kan bedrijven van alle websites in het dialoogvenster *Bedrijven* raster.

<u>Stappen om te reproduceren</u>:

1. Maak een aanvullende website, sla deze op en vergelijk deze.
1. Maak enkele bedrijven die zijn toegewezen aan verschillende websites.
1. Maak een beheerdersrol en stel het rolbereik in op de gemaakte website.
1. Creeer admin, en wijs het aan de gecreeerde rol toe.
1. Log in met een nieuwe beheerder.
1. Openen **[!UICONTROL Customers]** > **[!UICONTROL Companies]** en de lijst van ondernemingen in acht te nemen.

<u>Verwachte resultaten</u>:

De bedrijven die aan de aanvullende website zijn toegewezen, zijn zichtbaar in de *Bedrijven* raster.

<u>Werkelijke resultaten</u>:

Alle bedrijven zijn zichtbaar in de *Bedrijven* raster.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.