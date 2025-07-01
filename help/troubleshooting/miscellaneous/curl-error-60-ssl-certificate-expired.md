---
title: 'cURL-fout 60: SSL-certificaat verlopen'
description: 'Dit artikel laat zien hoe u kunt controleren wanneer een vertakking voor het laatst is geïmplementeerd na ontvangst van een cURL-fout 60: SSL-certificaat verlopen in de vertakkingen Master of Integratie op Adobe Commerce op de cloudinfrastructuur.'
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: dcaae51408534b82181b268f60905b123e240900
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# cURL-fout 60: SSL-certificaat verlopen

In dit artikel wordt getoond hoe u kunt controleren wanneer de laatste keer dat een vertakking is geïmplementeerd na ontvangst van een `cURL error 60` : [!DNL SSL certificate] verlopen in de vertakkingen [!DNL Master] of [!DNL Integration] op Adobe Commerce op een cloudinfrastructuur.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, [ alle gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Oorzaak

[!DNL SSL certificates] in deze vertakkingen is slechts geldig gedurende 30 dagen, en de vertakking kan niet in meer dan 30 dagen zijn herschikt.

De fout ziet er ongeveer als volgt uit:

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

>[!NOTE]
>
>Deze certificaten worden niet ondertekend door bekende externe certificeringsinstanties (CA&#39;s) zoals [!DNL Let's Encrypt] of [!DNL DigiCert] . Ze worden door het Adobe-platform beheerd voor test- en ontwikkelingsdoeleinden en worden mogelijk niet standaard vertrouwd in browsers of mobiele apparaten, tenzij u expliciet vertrouwt op de basis die het certificaat uitgeeft.

## Oplossing

Controle toen de laatste tijd de tak werd opgesteld. Als over de drempel van 30 dagen, dan herstelt de tak.

Twee methodes om te controleren wanneer de laatste plaatsing werd uitgevoerd:

* [ Methode 1: Gebruik  [!DNL magento-cloud]  CLI ](#meth2).
* [ Methode 2: Open  [!DNL Project URL]](#meth3).

Als de implementatie is voltooid, wordt [!DNL SSL certificate] automatisch vernieuwd.

Als de plaatsing ontbreekt en u hulp nodig die het oplossen, [ een steunkaartje ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=nl-NL#submit-ticket) oplost.

### Methode 1: [!DNL magento-cloud] CLI gebruiken {#meth2}

Voer deze opdracht uit: `magento-cloud activity:list --type=environment.push`

### Methode 2: Open het dialoogvenster [!DNL Project URL] {#meth3}

Ga bijvoorbeeld naar: `https://demo.magento.cloud/#/projects/<project>/environments/<environment>` en controleer wanneer de laatste implementatie is uitgevoerd.

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [ Cloud Manager API: SSLCcertificates ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [ Opstelling snel: Verlening SSL/TLS certificaten ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)

In onze kennisbasis voor ondersteuning:

* [ de informatie van de het certificaatvervaldatum van de Douane SSL ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html?lang=nl-NL)
* [ SSL (TLS) certificaten voor Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html?lang=nl-NL)
