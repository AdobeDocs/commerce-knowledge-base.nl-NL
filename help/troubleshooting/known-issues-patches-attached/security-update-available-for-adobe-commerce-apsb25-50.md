---
title: Beveiligingsupdate beschikbaar voor Adobe Commerce - [!DNL APSB25-50]
promoted: true
description: Pas een Geïsoleerd flard toe om  [!DNL critical and important vulnerabilities]  voor Adobe Commerce 2.4.8, 2.4.7-p5, 2.4.6-p10, 2.4.5-p12, 2.4.4-p13, en vroegere versies te verhelpen.
feature: Compliance, Security
role: Developer
source-git-commit: 9df7dee77bec7ffe4323f21e44d555338a0b1934
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Beveiligingsupdate beschikbaar voor Adobe Commerce - [!DNL APSB25-50]

Op 10 juni 2025 heeft Adobe een regelmatig geplande beveiligingsupdate uitgebracht voor Adobe Commerce en Magento Open Source. Deze update verhelpt [[!DNL critical]  en  [!DNL important] ](https://helpx.adobe.com/nl/security/severity-ratings.html) kwetsbaarheid. Een succesvolle benutting van deze kwetsbaarheden kan leiden tot het omzeilen van beveiligingsfuncties, escalatie van bevoegdheden en het uitvoeren van willekeurige code.

Meer informatie kan in het [ Bulletin van de Veiligheid van Adobe ([!DNL APSB25-50]) hier ](https://helpx.adobe.com/nl/security/products/magento/apsb25-50.html) worden gevonden.

>[!NOTE]
>
>**helpen ervoor zorgen dat de sanering voor [!DNL CVE-2025-47110] die in het veiligheidsbulletin hierboven wordt vermeld, zo snel mogelijk kan worden toegepast, heeft Adobe ook een geïsoleerd flard vrijgegeven dat [!DNL CVE-2025-47110] oplost. Dit staat verkopers toe om de moeilijke situatie geïsoleerd met minder risico&#39;s van vertraging toe te passen toe te schrijven aan potentiële integratiekwesties.**

**gelieve de recentste veiligheidsupdates toe te passen zo spoedig mogelijk. Als u dit niet doet, zult u aan deze veiligheidskwesties kwetsbaar zijn, en Adobe zal beperkte middelen hebben helpen de kwestie verder oplossen.**

U kunt meer over [ lezen ons geïsoleerde proces van de flardplaatsing hier.](https://business.adobe.com/blog/introducing-enhanced-security-patch-deployment-and-communications-in-adobe-commerce)

>[!NOTE]
>
>Voor Adobe Commerce op Managed Services-klanten kan uw Customer Success Engineer aanvullende richtlijnen geven voor het toepassen van de patch.

>[!NOTE]
>
>Neem contact op met de ondersteuningsservices als u problemen ondervindt bij het toepassen van de beveiligingspatch/de geïsoleerde patch.

Als herinnering, kunt u [ de recentste updates van de Veiligheid hier vinden beschikbaar voor Adobe Commerce.](https://helpx.adobe.com/nl/security/products/magento.html)

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden):

* 2.4.8.
* 2.4.7-p5 en eerdere versies
* 2.4.6-p10 en eerder
* 2.4.5-p12 en eerder
* 2.4.4-p13 en eerder

## Problemen

### I. CVE-2025-47110: Opgeslagen XSS via Server-Side Template Injection in Adobe Commerce 2.4.7-p4

<u> beïnvloedde producten en versies </u>:

Adobe Commerce (alle implementatiemethoden):

* 2.4.8.
* 2.4.7-p5 en eerdere versies
* 2.4.6-p10 en eerder
* 2.4.5-p12 en eerder
* 2.4.4-p13 en eerder

<u> Oplossing </u>:

Voor Adobe Commerce-versies:

* 2.4.8.
* 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4, 2.4.7-p5
* 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p10
* 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2 4.5-p11, 2.4.5-p12
* 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2 4.4-p11, 2.4.4-p12, 2.4.4-p13

**pas het volgende geïsoleerde flard of verbetering op het recentste veiligheidspatch toe.**

* **[VULN-31609_2.4.X.patch](assets/VULN-31609_2.4.X_patch.zip)**

### II. VULN-31547: Gereflecteerde XSS in marketplace.magento.com + één-klik ATO kwestie die IMS instanties beïnvloedt

<u> beïnvloedde producten en versies </u>:

Adobe Commerce (alle implementatiemethoden):

* 2.4.8.

<u> Oplossing </u>:

Voor Adobe Commerce-versies:

* 2.4.8.

**pas het volgende geïsoleerde flard of verbetering op het recentste veiligheidspatch toe.**

* **[VULN-31547_2.4.8.patch](assets/VULN-31547_2.4.8_patch.zip)**

## Hoe wordt de geïsoleerde pleister aangebracht

Pak het dossier uit en zie [ hoe te om een componentenflard toe te passen die door Adobe ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=nl-NL) in onze basis van steunkennis voor instructies wordt verstrekt.

## Alleen voor Adobe Commerce op Cloud-handelaren - Hoe kan ik zien of de geïsoleerde patches zijn aangebracht?

Aangezien het niet mogelijk is om eenvoudig te controleren of de uitgave is gerepareerd, kunt u beter controleren of de [!DNL CVE-2025-47110] geïsoleerde patch correct is toegepast.

>[!NOTE]
>
><u> u kunt dit doen door de volgende stappen te nemen, gebruikend het dossier `VULN-27015-2.4.7_COMPOSER.patch` **als VOORBEELD**</u>:

1. [ installeer het Hulpmiddel van de Patches van de Kwaliteit ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL).
1. Voer de opdracht uit:<br>
   ![ cve-2024-34102-tell-if-patch-applied-code ](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. U zou output gelijkend op dit moeten zien, waar VULN-27015 de *Toegepaste* status terugkeert:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## Beveiligingsupdates

Beveiligingsupdates beschikbaar voor Adobe Commerce:

* [ Bulletin van de Veiligheid van Adobe ([!DNL APSB25-50]) ](https://helpx.adobe.com/nl/security/products/magento/apsb25-50.html)
* [ De recentste updates van de Veiligheid beschikbaar voor Adobe Commerce ](https://helpx.adobe.com/nl/security/products/magento.html)
