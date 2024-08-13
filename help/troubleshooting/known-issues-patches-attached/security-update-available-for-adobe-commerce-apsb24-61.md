---
title: Beveiligingsupdate beschikbaar voor Adobe Commerce - [!DNL APSB24-61]
promoted: true
description: Pas een Geïsoleerd flard toe om  [!DNL CVE-2024-39397]  voor Adobe Commerce 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10, en vroegere slechts lopende versieinstanties te verhelpen  [!DNL Apache].
feature: Compliance, Security
role: Developer
source-git-commit: 76ff7669a0a57925a176e08031e0789ced0a7f0e
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Beveiligingsupdate beschikbaar voor Adobe Commerce - [!DNL APSB24-61]

Op 13 augustus 2024 heeft Adobe een regelmatig geplande beveiligingsupdate uitgebracht voor de plug-in Adobe Commerce, Magento Open Source en Adobe Commerce Webhooks.
Deze update verhelpt [[!DNL critical, important], en  [!DNL moderate] ](https://helpx.adobe.com/security/severity-ratings.html) kwetsbaarheid. Succesvolle uitbuiting kan leiden tot willekeurige code-uitvoering, willekeurig lezen in een bestandssysteem, het omzeilen van beveiligingsfuncties en escalatie van bevoegdheden. Het bulletin is [ Bulletin van de Veiligheid van de Adobe ([!DNL APSB24-61]) ](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

>[!NOTE]
>
>**[!DNL CVE-2024-39397]in het bovenstaande beveiligingsbulletin is alleen van toepassing wanneer u de [!DNL Apache] -webserver gebruikt.** Om ervoor te zorgen dat de oplossing voor deze kwetsbaarheid zo snel mogelijk kan worden toegepast, heeft de Adobe ook een geïsoleerde patch vrijgegeven die [!DNL CVE-2024-39397] verhelpt.

**gelieve de recentste veiligheidsupdates toe te passen zo spoedig mogelijk. Als u dit nalaat, zult u aan deze veiligheidskwesties kwetsbaar zijn, en de Adobe zal beperkte middelen hebben helpen oplossen.**

>[!NOTE]
>
>Neem contact op met de ondersteuningsservices als u problemen ondervindt bij het toepassen van de beveiligingspatch/de geïsoleerde patch.

## Betrokken producten en versies

Adobe Commerce op Cloud, Adobe Commerce op locatie en Magento Open Source:

* 2.4.7-p1 en lager
* 2.4.6-p6 en eerdere versies
* 2.4.5-p8 en eerder
* 2.4.4-p9 en eerder

## Oplossing voor Adobe Commerce op Cloud, Adobe Commerce on-premisse software en Magento Open Source

Om de kwetsbaarheid voor de betrokken producten en versies te helpen oplossen, moet u de [!DNL CVE-2024-39397] geïsoleerde patch toepassen.

## Geïsoleerde patchdetails

Gebruik de volgende bijgevoegde geïsoleerde pleister:

* [acsd-60551-composer-patch.zip](assets/acsd-60551-composer-patch.zip)

## Hoe wordt de geïsoleerde pleister aangebracht

Pak het dossier uit en zie [ hoe te om een componentenflard toe te passen die door Adobe ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in onze basis van steunkennis voor instructies wordt verstrekt.

## Alleen voor Adobe Commerce op Cloud-handelaren - Hoe kan ik zien of de geïsoleerde patches zijn aangebracht?

Aangezien het niet mogelijk is om eenvoudig te controleren of de uitgave is gerepareerd, kunt u beter controleren of de [!DNL CVE-2024-39397] geïsoleerde patch correct is toegepast.

<u> u kunt dit doen door de volgende stappen te nemen, gebruikend het dossier `VULN-27015-2.4.7_COMPOSER.patch` als voorbeeld </u>:

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

* [ Bulletin van de Veiligheid van de Adobe ([!DNL APSB24-61]) ](https://helpx.adobe.com/security/products/magento/apsb24-61.html)
