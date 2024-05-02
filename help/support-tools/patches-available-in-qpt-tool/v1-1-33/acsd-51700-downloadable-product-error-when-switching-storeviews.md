---
title: 'ACSD-51700: Fout bij het schakelen tussen winkelweergaven op downloadbare pagina voor productbewerking.'
description: Pas de ACSD-51700-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een fout optreedt bij het schakelen tussen de winkelweergaven op een downloadbare productbewerkingspagina in de beheerder.
feature: Products
role: Admin
exl-id: 652876a5-275d-437f-9cb3-baf4e7b23aae
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51700: fout bij het schakelen tussen winkelweergaven op de downloadbare pagina voor productbewerking

De ACSD-51700-patch verhelpt het probleem waarbij een fout optreedt bij het schakelen tussen de winkelweergaven op een downloadbare productbewerkingspagina in de beheerder. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51700. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

## Probleem

Er treedt een fout op wanneer wordt geschakeld naar een andere winkelweergave op een downloadbare productbewerkingspagina in de beheerder.

<u>Stappen om te reproduceren</u>:

1. Een downloadbaar product met een naam maken, [!DNL SKU]en prijs. Voeg geen koppelingen toe en sla het product op.
1. Schakel van alle winkelweergaven over naar de standaardwinkelweergave.
1. Maak een koppeling voor het downloadbare product en sla deze op.
1. Schakel van de standaardwinkelweergave naar alle winkelweergaven.

<u>Verwachte resultaten</u>:

De gekoppelde producten zijn zichtbaar.

<u>Werkelijke resultaten</u>:

De volgende fout wordt weergegeven:

*Vervangen functionaliteit: number_format(): Het doorgeven van null aan parameter #1 ($num) van het type float is afgekeurd in vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php op regel 228*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
