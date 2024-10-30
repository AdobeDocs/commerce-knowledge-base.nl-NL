---
title: Beveiligingsupdate beschikbaar voor Adobe Commerce - [!DNL APSB24-73]
promoted: true
description: Pas een Geïsoleerd flard toe om  [!DNL critical, important, and moderate vulnerabilities]  voor Adobe Commerce 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10, en vroegere versies slechts instanties te verhelpen die  [!DNL B2B]  module in werking stellen.
feature: Compliance, Security
role: Developer
source-git-commit: 483589be81e55f818f5cf93cccff2ffcbb5763cf
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Beveiligingsupdate beschikbaar voor Adobe Commerce - [!DNL APSB24-73]

Op 8 oktober 2024 heeft Adobe een regelmatig geplande beveiligingsupdate uitgebracht voor Adobe Commerce en [!DNL Adobe Commerce Webhooks Plugin] .
Deze update verhelpt [[!DNL critical, important], en  [!DNL moderate] ](https://helpx.adobe.com/security/severity-ratings.html) kwetsbaarheid. Succesvolle uitbuiting kan leiden tot willekeurige code-uitvoering, willekeurig lezen in een bestandssysteem, het omzeilen van beveiligingsfuncties en escalatie van bevoegdheden. Het bulletin is [ Bulletin van de Veiligheid van de Adobe ([!DNL APSB24-73]) ](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

>[!NOTE]
>
>**[!DNL CVE-2024-45115]in het bovenstaande beveiligingsbulletin is alleen van toepassing wanneer u de module [!DNL B2B] gebruikt.** Om ervoor te zorgen dat de oplossing voor deze kwetsbaarheid zo snel mogelijk kan worden toegepast, heeft de Adobe ook een geïsoleerde patch vrijgegeven die [!DNL CVE-2024-45115] verhelpt.

**gelieve de recentste veiligheidsupdates toe te passen zo spoedig mogelijk. Als u dit nalaat, zult u aan deze veiligheidskwesties kwetsbaar zijn, en de Adobe zal beperkte middelen hebben helpen oplossen.**

>[!NOTE]
>
>Neem contact op met de ondersteuningsservices als u problemen ondervindt bij het toepassen van de beveiligingspatch/de geïsoleerde patch.

## Betrokken producten en versies

Adobe Commerce on Cloud en Adobe Commerce in de gebouwen:

* 2.4.7-p2 en lager
* 2.4.6-p7 en eerdere versies
* 2.4.5-p9 en eerder
* 2.4.4-p10 en eerder

B2B:

* 1.4.2-p2 en lager
* 1.3.5-p7 en eerdere versies
* 1.3.4-p9 en eerder
* 1.3.3-p10 en eerder


## Oplossing voor Adobe Commerce on Cloud en Adobe Commerce on-premisse software

Om de kwetsbaarheid voor de betrokken producten en versies te helpen oplossen, moet u de [!DNL CVE-2024-45115] geïsoleerde patch toepassen.

## Geïsoleerde patchdetails

Gebruik de volgende bijgevoegde geïsoleerde pleister:

[vuln-26510-composer-patch.zip](assets/vuln-26510-composer-patch.zip)

## Hoe wordt de geïsoleerde pleister aangebracht

Pak het dossier uit en zie [ hoe te om een componentenflard toe te passen die door Adobe ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in onze basis van steunkennis voor instructies wordt verstrekt.

## Alleen voor Adobe Commerce op Cloud-handelaren - Hoe kan ik zien of de geïsoleerde patches zijn aangebracht?

Aangezien het niet mogelijk is om eenvoudig te controleren of de uitgave is gerepareerd, kunt u beter controleren of de [!DNL CVE-2024-45115] geïsoleerde patch correct is toegepast.

<u> u kunt dit doen door de volgende stappen te nemen, gebruikend het dossier `VULN-27015-2.4.7_COMPOSER.patch` **als voorbeeld**</u>:

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

* [ Bulletin van de Veiligheid van de Adobe ([!DNL APSB24-73]) ](https://helpx.adobe.com/security/products/magento/apsb24-73.html)
