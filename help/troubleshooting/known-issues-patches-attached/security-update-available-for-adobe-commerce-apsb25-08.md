---
title: Beveiligingsupdate beschikbaar voor Adobe Commerce - [!DNL APSB25-08]
promoted: true
description: Pas een Geïsoleerd flard toe om  [!DNL critical, important, and moderate vulnerabilities]  voor Adobe Commerce 2.4.8-beta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11, en vroegere versies te verhelpen.
feature: Compliance, Security
role: Developer
exl-id: 567e6ad2-704e-461f-a54d-75f6bd96e996
source-git-commit: d669c097767b5855c6bd747a0ab11b3520f405a0
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Beveiligingsupdate beschikbaar voor Adobe Commerce - [!DNL APSB25-08]

Op 11 februari 2025 heeft Adobe een regelmatig geplande beveiligingsupdate uitgebracht voor Adobe Commerce en Magento Open Source. Deze update verhelpt [[!DNL critical, important], en  [!DNL moderate] ](https://helpx.adobe.com/security/severity-ratings.html) kwetsbaarheid. Een succesvolle benutting van deze kwetsbaarheden kan leiden tot het uitvoeren van willekeurige code, het omzeilen van beveiligingsfuncties en het doorverwijzen van bevoegdheden. Meer informatie kan in het [ Bulletin van de Veiligheid van Adobe ([!DNL APSB25-08]) hier ](https://helpx.adobe.com/security/products/magento/apsb25-08.html) worden gevonden.

>[!NOTE]
>
>**helpen ervoor zorgen dat de sanering voor [!DNL CVE-2025-24434], die in het veiligheidsbulletin hierboven wordt vermeld, zo snel mogelijk kan worden toegepast, heeft Adobe ook een geïsoleerde flard vrijgegeven die [!DNL CVE-2025-24434] oplost. Dit staat verkopers toe om de moeilijke situatie geïsoleerd met minder risico&#39;s van vertraging toe te passen toe te schrijven aan potentiële integratiekwesties.**

**gelieve de recentste veiligheidsupdates toe te passen zo spoedig mogelijk. Als u dit niet doet, zult u aan deze veiligheidskwesties kwetsbaar zijn, en Adobe zal beperkte middelen hebben helpen de kwestie verder oplossen.**

>[!NOTE]
>
>Neem contact op met de ondersteuningsservices als u problemen ondervindt bij het toepassen van de beveiligingspatch/de geïsoleerde patch.

## Betrokken producten en versies

Adobe Commerce op Cloud-infrastructuur, Adobe Commerce op locatie en Magento Open Source:

* 2.4.8-bèta1 en lager
* 2.4.7-p3 en eerdere versies
* 2.4.6-p8 en eerder
* 2.4.5-p10 en eerder
* 2.4.4-p11 en eerder

## Oplossing voor Adobe Commerce op Cloud, Adobe Commerce op locatie en Magento Open Source-software

Om de kwetsbaarheid voor de betrokken producten en versies te helpen oplossen, moet u de [!DNL CVE-2025-24434] Geïsoleerde patch toepassen, afhankelijk van uw Adobe Commerce/Magento Open Source-versie.

## Geïsoleerde patchdetails

Gebruik de volgende gekoppelde, geïsoleerde patches, afhankelijk van uw Adobe Commerce/Magento Open Source-versie:

### Voor versie 2.4.8-bèta1:

* [vuln-28982-2-4-8x-v2-composer-patch.zip](assets/vuln-28982-2-4-8x-v2-composer-patch.zip)

### Voor versies 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3:

* [vuln-28982-2-4-7x-v2-composer-patch.zip](assets/vuln-28982-2-4-7x-v2-composer-patch.zip)

### Voor versies 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8:

* [vuln-28982-2-4-6x-v2-composer-patch.zip](assets/vuln-28982-2-4-6x-v2-composer-patch.zip)

### Voor de versies 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10:

* [vuln-28982-2-4-5x-v2-composer-patch.zip](assets/vuln-28982-2-4-5x-v2-composer-patch.zip)

### Voor versies 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p1 0, 2.4.4-p11:

* [vuln-28982-2-4-4x-v2-composer-patch.zip](assets/vuln-28982-2-4-4x-v2-composer-patch.zip)


## Hoe wordt de geïsoleerde pleister aangebracht

Pak het dossier uit en zie [ hoe te om een componentenflard toe te passen die door Adobe ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in onze basis van steunkennis voor instructies wordt verstrekt.

## Alleen voor Adobe Commerce op Cloud-handelaren - Hoe kan ik zien of de geïsoleerde patches zijn aangebracht?

Aangezien het niet mogelijk is om eenvoudig te controleren of de uitgave is gerepareerd, kunt u beter controleren of de [!DNL CVE-2025-24434] geïsoleerde patch correct is toegepast.

>[!NOTE]
>
><u> u kunt dit doen door de volgende stappen te nemen, gebruikend het dossier `VULN-27015-2.4.7_COMPOSER.patch` **als voorbeeld**</u>:

1. [ installeer het Hulpmiddel van de Patches van de Kwaliteit ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
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

* [ Bulletin van de Veiligheid van Adobe ([!DNL APSB25-08]) ](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [ de recentste updates van de Veiligheid beschikbaar voor Adobe Commerce) ](https://helpx.adobe.com/security/products/magento.html)