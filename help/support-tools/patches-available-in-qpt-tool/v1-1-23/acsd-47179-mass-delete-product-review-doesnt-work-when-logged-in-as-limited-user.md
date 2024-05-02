---
title: "ACSD-47179: het massaal verwijderen van productoverzichten werkt niet wanneer aangemeld als beperkte gebruikersrol"
description: Pas de ACSD-47179-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het massaal verwijderen van productoverzichten niet werkt wanneer u bent aangemeld als een beperkte gebruikersrol.
exl-id: 85d7ce63-7dd6-4df4-b314-278d18e69fbb
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-47179: het massaal verwijderen van productoverzichten werkt niet wanneer het programma als beperkte gebruikersrol wordt geopend

De ACSD-47179-patch verhelpt het probleem dat het massaal verwijderen van productoverzichten niet werkt wanneer u bent aangemeld als een beperkte gebruikersrol. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 is geïnstalleerd. De patch-id is ACSD-47179. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De massale schrapping van productoverzichten werkt niet wanneer het programma geopend als beperkte gebruikersrol.

<u>Stappen om te reproduceren</u>:

1. Maak een secundaire website.
1. Maak een gebruikersrol die beperkt is tot de secundaire website met volledige toestemming voor de volgende secties:
   * Catalogus
   * Klant
   * Marketing
1. Maak een product en wijs het toe aan de secundaire website.
1. Voeg twee recensies toe aan het product vanaf de voorzijde.
1. Aanmelden bij de [!DNL Commerce] Beheer met behulp van de beperkte beheerder die zojuist door de gebruiker is gemaakt.
1. Probeer verwijderde revisies in behandeling opnieuw te publiceren.

<u>Verwachte resultaten</u>:

Een beheerder met voldoende machtigingen kan het verwijderen van revisies in behandeling openbaar maken.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op: _Er is iets misgegaan. Uitzondering die in support_report.log wordt gegenereerd_

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
