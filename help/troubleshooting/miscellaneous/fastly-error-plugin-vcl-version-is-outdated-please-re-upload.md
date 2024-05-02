---
title: '''Fastly Error: Plugin VCL version is verouderd! Wilt u het bestand opnieuw uploaden?'
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

Dit artikel biedt een oplossing voor wanneer het bericht &quot;*De versie van de insteekmodule VCL is verouderd! Upload het bestand opnieuw.*&quot; in Fastly Configuration, in the Commerce Admin, due to not have installed the latest Fastly module.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.2.x, 2.3.x<br>
Kortom: deze fout kan van invloed zijn op alle versies van de module Snelheid, behalve op de meest recente. Voor informatie over de meest recente versie raadpleegt u [Opmerkingen bij de release snel](https://github.com/fastly/fastly-magento2/releases) op GitHub.

## Probleem

1. Meld u aan bij het deelvenster Commerce Admin.
1. Navigeren naar **Winkels** > **Configuratie** > **Geavanceerd** > **Systeem** > **Volledige paginacache**   **Snel cache.**
1. In de **Automatisch uploaden en service activeren** in de sectie wordt een &quot;*De versie van de insteekmodule VCL is verouderd! Upload het bestand opnieuw.*&quot;kennisgeving.
1. U probeert de VCL-fragmenten te uploaden door op de knop &quot;VCL snel uploaden naar snel&quot; te klikken, maar u ziet nog steeds de waarschuwing &quot;*De versie van de insteekmodule VCL is verouderd! Upload het bestand opnieuw.*&quot;

## Oorzaak

De snelste extensie is bijgewerkt (samen met een gebundelde VCL-configuratie en sjablonen), maar de bijgewerkte VCL-configuratie is niet geüpload naar de Fastly-service. Wanneer u de Adobe Commerce-module bijwerkt `Fastly_Cdn`, moet u een bijgewerkte configuratie van VCL aan Fastly opnieuw uploaden.

## Oplossing

1. Controleer of u de meest recente ECE-gereedschappen hebt geïnstalleerd en op het tabblad [huidige versie](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html) in onze ontwikkelaarsdocumentatie. ECE-Tools heeft een versie van het pakket Fastly in zijn afhankelijkheden.

   Dit is mogelijk niet de nieuwste versie van de snelplug-in, maar het is waarschijnlijk een nieuwere versie dan de versie die u momenteel hebt geïnstalleerd. Het is aan te raden de nieuwste ECE-tools te installeren.

1. Als de huidige versie van ECE-Tools niet wordt gebruikt, voert u de volgende stappen uit om [upgrade](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) in onze ontwikkelaarsdocumentatie.
1. Nadat u ECE-Hulpmiddelen hebt bevorderd, controleer of hebt u nu een huidige versie van [Snelle plug-in](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets) geïnstalleerd.
1. Als de snelplug-in niet de huidige versie is, voert u de volgende stappen uit: [upgrade de insteekmodule naar de meest recente versie](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

* Voor informatie over vestiging en het vormen van Fastly, zie [Services voor snel configureren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) in onze ontwikkelaarsdocumentatie.
* Voor algemene informatie over Snelheid raadpleegt u [fastly.com](https://www.fastly.com/).
