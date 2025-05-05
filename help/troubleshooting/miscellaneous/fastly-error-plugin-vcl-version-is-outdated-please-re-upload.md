---
title: 'Fastly Error: Plugin VCL version is verouderd! Please re-Upload'
description: Dit artikel verstrekt een oplossing voor wanneer u het bericht "*Versie van de Insteekmodule VCL verouderd ziet! Upload het bestand opnieuw.*" in Fastly Configuration, in Commerce Admin, omdat het niet de nieuwste snelste module heeft geïnstalleerd.
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Fastly Error: Plugin VCL version is verouderd! Please re-Upload

Dit artikel verstrekt een oplossing voor wanneer u het bericht &quot;*de versie van de Insteekmodule VCL verouderd ziet! Upload het bestand opnieuw.*&quot; in Fastly Configuration, in de Commerce Admin, omdat de nieuwste snelste module niet is geïnstalleerd.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.2.x., 2.3.x <br>
Kortom: deze fout kan van invloed zijn op alle versies van de module Snelheid, behalve op de meest recente. Voor informatie over de recentste versie, zie {de nota&#39;s van de versie van 0} de snelste versie [&#128279;](https://github.com/fastly/fastly-magento2/releases) op GitHub.

## Probleem

1. Meld u aan bij het deelvenster Commerce Admin.
1. Navigeer aan **Opslag** > **Configuratie** > **Geavanceerd** > **Systeem** > **Volledige het Geheime voorgeheugen van de Pagina**   **Snelle Geheime voorgeheugen.**
1. In de **Automatische Upload &amp; de Activatie van de Dienst** sectie, zal er a &quot;*versie van de Insteekmodule VCL verouderd zijn! Upload het bestand opnieuw.*&quot;.
1. U probeert om de fragmenten te uploaden VCL door op de &quot;Upload VCL aan Fastly&quot;knoop te klikken maar u ziet nog de waarschuwing &quot;*versie van de Insteekmodule VCL is verouderd! Please re-Upload.*&quot;

## Oorzaak

De snelste extensie is bijgewerkt (samen met een gebundelde VCL-configuratie en sjablonen), maar de bijgewerkte VCL-configuratie is niet geüpload naar de Fastly-service. Wanneer u de Adobe Commerce-module `Fastly_Cdn` bijwerkt, moet u een bijgewerkte VCL-configuratie opnieuw naar Fastly uploaden.

## Oplossing

1. Controle dat u recentste ECE-Hulpmiddelen hebt geïnstalleerd en bij de [ huidige versie ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie. ECE-Tools heeft een versie van het pakket Fastly in zijn afhankelijkheden.

   Dit is mogelijk niet de nieuwste versie van de snelplug-in, maar het is waarschijnlijk een nieuwere versie dan de versie die u momenteel hebt geïnstalleerd. Het is aan te raden de nieuwste ECE-tools te installeren.

1. Als u niet op de huidige versie van ECE-Hulpmiddelen bent, volg deze stappen aan [ verbetering ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
1. Nadat u ECE-Hulpmiddelen hebt bevorderd, controleer als u nu een huidige versie van de [ Snelle geïnstalleerde stop ](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets) hebt.
1. Als de Snelle stop niet de huidige versie is, volg deze stappen aan [ verbetering de stop aan de huidigste versie ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=nl-NL#upgrade-the-fastly-module) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

* Voor informatie over vestiging en het vormen snel, zie [ de Snelle diensten ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie vormen.
* Voor algemene informatie over Fastly, zie [ faals.com ](https://www.fastly.com/).
