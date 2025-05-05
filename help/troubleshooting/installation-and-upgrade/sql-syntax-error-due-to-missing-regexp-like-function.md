---
title: Upgrade naar B2B 1.5.2 mislukt vanwege SQL-syntaxisfout bij ontbrekende functie REGEXP_LIKE
description: Dit artikel verstrekt hotfix voor de kwestie waar een SQL syntaxisfout voorkomt toe te schrijven aan de ontbrekende functie REGEXP_LIKE wanneer het proberen om de company_structure lijst bij te werken.
feature: B2B, Upgrade
role: Admin, Developer
exl-id: c5fe316c-99e3-482e-80b5-25aaae371230
source-git-commit: 04e17dfdf143e233eb2767064c1328990c899eda
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Upgrade naar B2B 1.5.2 mislukt vanwege SQL-syntaxisfout bij ontbrekende functie REGEXP_LIKE

>[!INFO]
>
>Als u een prestatieskwestie wanneer het bevorderen van de `Magento_Company` module na het bijwerken aan B2B 1.5.2 ervaart, pas in bijlage [ ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch ](assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip) toe.
>
>Voor meer informatie, verwijs naar [ kwestie van Prestaties in Magento_Company moduleverbetering na B2B 1.5.2 update ](/help/troubleshooting/installation-and-upgrade/magento-company-module-upgrade-performance-issue.md) in de kennisbasis van Adobe Commerce.

Dit artikel bevat een hotfix voor de SQL-syntaxisfout die optreedt als de functie `REGEXP_LIKE` ontbreekt bij het bijwerken van de tabel `company_structure` .

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.4.6-px + B2B 1.5.2 met [!DNL MariaDB] 10.6
* Adobe Commerce (alle implementatiemethoden) 2.4.7-px + B2B 1.5.2 met [!DNL MariaDB] 10.6

## Probleem

De upgrade naar B2B versie 1.5.2 mislukt door een SQL-syntaxisfout vanwege de ontbrekende `REGEXP_LIKE` -functie wanneer u probeert de `company_structure` -tabel bij te werken.

<u> Eerste vereisten </u>:

* MariaDB 10.6
* Adobe Commerce 2.4.6x of 2.4.7x
* B2B versie 1.5.0 of 1.5.1

<u> Stappen om </u> te reproduceren:

1. Wijs een bedrijf aan een moederbedrijf toe om bedrijfshiërarchie te vestigen. Verwijs naar [ leiden de Hiërarchie van het Bedrijf ](https://experienceleague.adobe.com/nl/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) in de gids van Adobe Commerce B2B voor meer informatie.
1. Upgrade B2B naar versie 1.5.2.

<u> Verwachte resultaten </u>:

De upgrade is voltooid.

<u> Ware resultaten </u>:

`bin/magento setup:upgrade` mislukt met de volgende fout:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^123(/.+)?$'))
```

## Oplossing

Voer de volgende stappen uit om het probleem op te lossen:

1. Werk de B2B-module bij naar versie 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Pas [ ACSD-65540_B2B_1.5.2.zip ](assets/ACSD-65540_B2B_1.5.2.zip) flard in bijlage toe. Verwijs naar [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis voor instructies wordt verstrekt.
1. Voer `bin/magento setup:upgrade` uit.

### Een patch toepassen met gebruik van Cloud Patches

Volg onderstaande stappen voor Adobe Commerce on Cloud-infrastructuur:

1. Werk de versie van de module `cloud-patches` bij naar versie 1.1.5:

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Leg de wijzigingen vast en duw deze om opnieuw te implementeren. Verwijs naar [ passen flarden ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) in onze gids Adobe Commerce op de Wolk voor instructies toe.
