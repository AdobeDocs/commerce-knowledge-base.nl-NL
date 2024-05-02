---
title: 'cURL error 60: SSL certificate expired'
description: 'Dit artikel laat zien hoe u kunt controleren wanneer de laatste keer dat een vertakking werd geïmplementeerd na ontvangst van een cURL-fout 60: SSL-certificaat verlopen in de vertakkingen Master of Integration op Adobe Commerce op een cloudinfrastructuur.'
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: 6f631ca35b663c386bca9efe6e56db266502c0b1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# cURL-fout 60: SSL-certificaat verlopen

Dit artikel toont hoe te controleren wanneer de laatste tijd een tak na het ontvangen van werd opgesteld `cURL error 60`: [!DNL SSL certificate] is verlopen in het [!DNL Master] of [!DNL Integration] vestigingen op Adobe Commerce op cloudinfrastructuur.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Oorzaak

De [!DNL SSL certificates] in die bijkantoren slechts 30 dagen geldig zijn en het bijkantoor mogelijk niet meer dan 30 dagen opnieuw is ingezet.

De fout ziet er ongeveer als volgt uit:

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

## Oplossing

Controle toen de laatste tijd de tak werd opgesteld. Als over de drempel van 30 dagen, dan herstelt de tak.

Twee methodes om te controleren wanneer de laatste plaatsing werd uitgevoerd:

* [Methode 1: Gebruik [!DNL magento-cloud] CLI](#meth2).
* [Methode 2: Open de [!DNL Project URL]](#meth3).

Als de implementatie met succes is voltooid, [!DNL SSL certificate] wordt automatisch verlengd.

Als de implementatie mislukt en u hulp nodig hebt om deze op te lossen, [een ondersteuningsticket indienen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

### Methode 1: Gebruik [!DNL magento-cloud] CLI {#meth2}

Voer deze opdracht uit: `magento-cloud activity:list`

### Methode 2: Open de [!DNL Project URL] {#meth3}

Ga bijvoorbeeld naar: `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`en controleer wanneer de laatste implementatie is uitgevoerd.

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [Cloud Manager-API: SSLC-certificaten](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Meteen instellen: SSL/TLS-certificaten leveren](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates)

In onze kennisbasis voor ondersteuning:

* [Aangepaste SSL-certificaatvervalgegevens](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html)
* [SSL-certificaten (TLS) voor Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html)
