---
title: 'ACSD-50512: Fout bij het bijwerken van de begindatum voor een downloadbare product-staging-update'
description: Pas de ACSD-51892-patch toe om het probleem met de Adobe Commerce-prestaties op te lossen wanneer de fout *De downloadbare koppeling is niet gerelateerd aan het product.Controleer de koppeling en probeer het opnieuw*, en dit gebeurt bij het bijwerken van de begindatum voor een downloadbare product-staging-update.
feature: Products, Staging
role: Admin
exl-id: 873357ef-49c3-48f8-a98e-41c48cb9ba8b
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-50512: Fout bij het bijwerken van de begindatum voor een downloadbare update voor productplaatsing

De ACSD-50512-patch verhelpt het probleem waarbij de fout optreedt *De downloadbare koppeling heeft geen betrekking op het product. De koppeling controleren en het opnieuw proberen*, vindt plaats bij het bijwerken van de begindatum voor een downloadbare update voor productplaatsing. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51502. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De fout *De downloadbare koppeling heeft geen betrekking op het product. De koppeling controleren en het opnieuw proberen*, vindt plaats bij het bijwerken van de begindatum voor een downloadbare update voor productplaatsing.

<u>Stappen om te reproduceren</u>:

1. Een downloadbaar product maken met *downloadbare koppelingen* en *voorbeeldkoppelingen*.
1. Maak een geplande update voor hetzelfde product en sla het product op.
1. Bewerk de vooraf geconfigureerde geplande update (vanuit stap 2) en wijzig de begindatum.
1. Sla de geplande update op.

<u>Verwachte resultaten</u>:

De wijzigingen in de geplande update worden opgeslagen.

<u>Werkelijke resultaten</u>:

De fout wordt weergegeven: *De downloadbare koppeling heeft geen betrekking op het product. Koppeling verifiëren en opnieuw proberen*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
