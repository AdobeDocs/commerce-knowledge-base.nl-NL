---
title: 'ACSD-50849: Het toevoegen van een nieuw product na het wissen van de cache resulteert in een onjuiste overeenkomst'
description: Pas de ACSD-50849-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het toevoegen van een nieuw product aan de categorie na het wissen van de cache resulteert in een onjuiste weergave van posities en selecties van de bestaande producten.
feature: Cache, Categories, Products
role: Admin
exl-id: 3c797bf4-45da-4500-8c06-8c1007249738
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-50849: het toevoegen van een nieuw product na het wissen van de cache resulteert in een onjuiste overeenkomst

De ACSD-50849-patch verhelpt het probleem dat het toevoegen van een nieuw product aan de categorie na het wissen van de cache resulteert in een onjuiste weergave van posities en selecties van de bestaande producten. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) QPT 1.1.32 is geïnstalleerd. De patch-id is ACSD-50849. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een nieuw product aan de categorie toevoegt nadat u de cache hebt gewist, komen de posities en selecties van de bestaande producten niet overeen.

<u>Stappen om te reproduceren</u>:

1. Maak twee producten.
1. Eén product aan een categorie toewijzen.
1. Open de categorie via de beheerder.
1. De cache opschonen `bin/magento cache:flush`.
1. Voeg het tweede product toe aan de categorie.

<u>Verwachte resultaten</u>:

De bestaande producten die in de categorie zijn toegewezen, worden niet automatisch verwijderd.

<u>Werkelijke resultaten</u>:

Het eerste (bestaande) product wordt automatisch verwijderd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
