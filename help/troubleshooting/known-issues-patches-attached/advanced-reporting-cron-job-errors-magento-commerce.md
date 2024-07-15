---
title: Geavanceerde rapportage van fouten met uitsnijdtaken Adobe Commerce
description: Dit artikel verstrekt flarden voor de Geavanceerde de baankwesties van de Rapportering cron in Adobe Commerce, die een 404 fout voor klanten kunnen veroorzaken die tot Geavanceerde Rapportering proberen toegang te hebben.
exl-id: c11a5faf-a243-411a-af0f-585a401e6e39
feature: Cache
role: Developer
source-git-commit: 6287e708c830680e04dd068b64cf63ca13ecdedb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Geavanceerde rapportage van fouten met uitsnijdtaken Adobe Commerce

Dit artikel verstrekt flarden voor de Geavanceerde de baankwesties van de Rapportering cron in Adobe Commerce, die een 404 fout voor klanten kunnen veroorzaken die tot Geavanceerde Rapportering proberen toegang te hebben.

## Betrokken producten en versies

Adobe Commerce (alle implementatieopties) 2.3.x

## Probleem

Een klant krijgt een fout van 404 wanneer hij probeert toegang te krijgen tot Advanced Reporting en er zijn fouten in de logboeken die aan `analytics_collect_data job` zijn gekoppeld.

## Compatibele versies van Magento&#39;s:

De patches zijn compatibel (maar lossen het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* [ MDVA-19391 \_EE\_2.3.1\_COMPOSER\_v1.patch ](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip): Adobe Commerce (alle plaatsingsopties) 2.3.1-2.3.4-p2
* [ MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1.patch ](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (alle plaatsingsopties) 2.3.0
* [ MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch ](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (alle plaatsingsopties) 2.3.0

## **Oplossing**

Als u het probleem wilt verhelpen, past u de relevante patch toe die aan dit artikel is gekoppeld. Klik op de volgende koppelingen om het te downloaden:

* Download [ MDVA-19391 \_EE\_2.3.1\_COMPOSER\_v1.patch ](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip)
* Download [ MDVA-15136 \_EE \_2.2.6\_COMPOSER\_v1.patch ](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)
* Download [ MDVA-18980 \_EE \_2.3.1 \_COMPOSER\_v1.patch ](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

Om te controleren welke pleister moet worden gebruikt:

<ol><li>Herzie de logboeken door het volgende bevel te gebruiken:<code>grep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz</code>
</li><li>Afhankelijk van de fout die u ziet, selecteert u een patch aan de hand van de gegevens in de volgende tabel.<table style="width: 826px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center">
<p>Fout</p>
</td>
<td class="wysiwyg-text-align-center">Reparatie</td>
</tr>
<tr>
<td>
<pre>report.CRITICAL: Error when running a cron job {"exception":"[object] (RuntimeException(code::
  0): Fout bij het uitvoeren van een uitsnijdtaak op /srv/public_html/vendor/magento/module-cron/Observer/ProcessCronQueueObserver.php:327,
  TypeError(code: 0): substr_count() verwacht dat parameter 1 een tekenreeks is, op basis van null
  op /srv/public_html/vendor/magento/module-page-builder-analytics/Model/ContentTypeUsageReportProvider.php:106)"}
  []</pre>OF<pre>report.ERROR: Cron Job analytics_collect_data heeft een fout: substr_count() verwacht
  parameter 1 als tekenreeks, null gegeven. Statistieken: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384}
  [] []</pre>
<p> </p>
</td>
<td>Pas <a href="assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch"> MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip </a> toe, ontruim geheim voorgeheugen en wacht 24 uren op de baan opnieuw te lopen en opnieuw te proberen.</td>
</tr>
<tr>
<td>
<p><em>Kan het bestand /tmp/analytics/tmp/../tmp/../tmp/../tmp/.../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/..../tmp/../tmp/../</em></p>
</td>
<td>Pas <a href="assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch"> MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip </a> toe, ontruim geheim voorgeheugen en wacht 24 uur op de baan opnieuw te lopen en opnieuw te proberen.</td>
</tr>
<tr>
<td><em>Geen geldig cijfer</em></td>
<td>Pas <a href="assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch"> MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip </a> toe, ontruim geheim voorgeheugen en wacht 24 uren op de baan opnieuw te lopen en opnieuw te proberen.</td>
</tr>
</tbody>
</table>
</li></ol>

## Hoe de pleister aanbrengen

Pak het dossier uit en volg instructies in [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) wordt verstrekt.

## Verwante lezing

[Het bestand kan niet worden verwijderd. Waarschuwing!unlink: bestands- of mapfout is niet beschikbaar in de beheerdersmap](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)
