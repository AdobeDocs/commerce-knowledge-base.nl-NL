---
title: Prestatiekwestie in de Magento_Company-module-upgrade na B2B 1.5.2-update
description: Dit artikel verstrekt hotfix voor de prestatieskwestie in de Magento_Company modulesverbetering na B2B 1.5.2 update, die de uitzonderlijk lange verwerkingstijd voor grote datasets in de company_structure lijst richt.
feature: B2B, Upgrade
role: Admin, Developer
source-git-commit: d06f0045b4c4c1615bd3abec963eb17fdee93860
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Prestatiekwestie in de Magento_Company-module-upgrade na B2B 1.5.2-update

Dit artikel biedt een hotfix voor het prestatieprobleem in de `Magento_Company` module-upgrade na de B2B 1.5.2-update, die de uitzonderlijk lange verwerkingstijd voor grote datasets (~100.000+ records) in de `company_structure` -tabel aanpakt.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.4.6-px + B2B 1.5.2
* Adobe Commerce (alle implementatiemethoden) 2.4.7-px + B2B 1.5.2
* Adobe Commerce (alle implementatiemethoden) 2.4.8 + B2B 1.5.2

## Probleem

Het bijwerken van de module `Magento_Company` na het bijwerken naar B2B 1.5.2 duurt te lang wanneer u een groot aantal records (~100.000+) in de tabel `company_structure` verwerkt.

<u> Eerste vereisten </u>:

* ACSD-65540_B2B_1.5.2.patch moet worden geïnstalleerd.
* Adobe Commerce 2.4.6 - 2.4.8
* B2B versie 1.5.0, 1.5.1 of B2B 1.5.2 met de ACSD-65540-patch toegepast

<u> Stappen om </u> te reproduceren:

1. Wijs een bedrijf aan een moederbedrijf toe om bedrijfshiërarchie te vestigen. Verwijs naar [ leiden de Hiërarchie van het Bedrijf ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) in de gids van Adobe Commerce B2B voor meer informatie.
1. Upgrade B2B naar versie 1.5.2.

<u> Verwachte resultaten </u>:

De upgrade is voltooid.

<u> Ware resultaten </u>:

Het bijwerken van de module `Magento_Company` duurt lang om te voltooien als de tabel `company_structure` veel records bevat.

## Oplossing

Voer de volgende stappen uit om het probleem op te lossen:

1. Werk de B2B-module bij naar versie 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Pas [ ACSD-65540_B2B_1.5.2.patch ](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2.zip) toe.

1. Pas [ ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch ](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip) in bijlage toe.
1. Voer `bin/magento setup:upgrade` uit nadat u de patch hebt toegepast.

### Hoe de pleister aanbrengen

Pak het dossier uit en zie [ hoe te om een componentenflard toe te passen die door Adobe ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) in onze basis van steunkennis voor instructies wordt verstrekt.

### Een patch toepassen met gebruik van Cloud Patches

Voor Adobe Commerce on Cloud-winkeliers voert u de volgende stappen uit:

1. Werk de versie van de cloudpatches bij naar 1.1.5 om de ACSD-65540_B2B_1.5.2.patch te installeren die als MCLOUD-13605 wordt gedistribueerd.

   >[!NOTE]
   >
   >Voer de volgende handelingen uit om te controleren of de patch al is geïnstalleerd:
   > `./vendor/bin/magento-patches -n status | grep MCLOUD-13605`

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Voeg de patch ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.2 toe aan de map `m2-hotfixes` .
1. Leg de wijzigingen vast en duw deze om herimplementatie en `bin/magento setup:upgrade` te starten. Verwijs naar [ passen flarden ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) in onze gids Adobe Commerce op de Wolk voor instructies toe.

## Gerelateerde lezing

* [ Verbetering aan B2B 1.5.2 ontbreekt met SQL syntaxisfout toe te schrijven aan het ontbreken van functie REGEXP_LIKE ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/sql-syntax-error-due-to-missing-regexp-like-function)
