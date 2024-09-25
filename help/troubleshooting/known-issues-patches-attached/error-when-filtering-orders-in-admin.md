---
title: Fout bij het filteren van orders in de beheerder
description: Dit artikel biedt een patch voor het Adobe Commerce-probleem, waarbij een fout optreedt bij het filteren van orders in Admin op datum, waarbij het bericht 'Integrity constraint violt 1052 Column 'created_at' wordt weergegeven waarbij de component dubbelzinnig is.
feature: Orders
role: Developer
source-git-commit: e5eb65b23afaed4658f8576c747f11a31a8ec1aa
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Fout bij het filteren van orders in de beheerder

Dit artikel verstrekt een flard voor de kwestie van Adobe Commerce waar een fout voorkomt wanneer het proberen om orden in Admin door datum te filtreren, tonend het bericht: *schending van de de beperkingsbeperking van de Integriteit: 1052 Kolom &quot;created_at&quot;waar de clausule dubbelzinnig* is.

## Betrokken versies

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7

## Probleem

Als u op datum orders in de beheerdersaccount filtert, wordt een fout geretourneerd.

The exception.log toont:

```SQL
report.CRITICAL: PDOException: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'created_at' in where clause is ambiguous in /path/to/magento/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
```

<u> Stappen om te reproduceren:</u>

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** .
   * De **[!UICONTROL Purchase Date Ascending]** -volgorde in het raster instellen OF
   * Stel **[!UICONTROL Purchase Date Filter]** in filters in.

1. Een fout verschijnt: *ging iets fout met verwerking van de standaardmening en wij hebben de filter aan zijn originele staat hersteld.*

## Oorzaak

Er is een probleem met de modules [!DNL PayPal Braintree] .

## Oplossing

U kunt dit probleem oplossen door de patch toe te passen die aan dit artikel is gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[bundle_3357_filter_order_in_admin_by_date_patch.zip](assets/bundle-3357-unable-to-filter-order-in-admin-by-date.zip)

De patch is compatibel met alle betrokken versies en versies.

## Hoe de pleister aanbrengen

Voor instructies, zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in de steunkennisbasis wordt verstrekt.
