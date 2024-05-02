---
title: 'ACSD-51630: veel systeemberichten vertragen het downloaden van Admin Pages'
description: Pas de ACSD-51630-patch toe om het Adobe Commerce-prestatieprobleem te verhelpen, waarbij het downloaden van Admin Pages wordt vertraagd door een grote hoeveelheid systeemberichten.
feature: Admin Workspace, System
role: Admin
exl-id: 28f85199-625e-4299-bbca-8d2fc75df602
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# ACSD-51630: veel systeemberichten vertragen het downloaden van beheerpagina&#39;s

De ACSD-51630-patch verhelpt het prestatieprobleem waarbij het downloaden van Admin Pages wordt vertraagd door een grote hoeveelheid systeemberichten. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.34 is geïnstalleerd. De patch-id is ACSD-51630. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Veel systeemberichten vertragen het downloaden van beheerpagina&#39;s

<u>Stappen om te reproduceren</u>:

1. Voer een groot aantal aanvragen (~50 kB) in bij DELETE `/rest/async/v1/products/ {sku}`.
1. Toegang tot alle **Beheerpagina**.

<u>Verwachte resultaten</u>:

Pagina wordt op een geschikte tijd geladen. Alleen berichten die worden weergegeven, moeten worden geladen.

<u>Werkelijke resultaten</u>:

Het laden van de pagina duurt te lang. Alle bestaande berichten worden geladen uit het gegevensbestand.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
