---
title: '''[!DNL Admin] aanmelden werkt niet - toegestane sessiemaximale grootte overschreden'
description: Los het probleem op wanneer u zich probeert aan te melden bij uw [!DNL Admin] en het formulier wordt vernieuwd en u kunt zich niet aanmelden.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 8718148f6d9a40c9a71484a7fbc818a626e825e1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# [!DNL Admin] aanmelden werkt niet - toegestane sessiegrootte is overschreden

Dit artikel biedt een oplossing voor het aanmelden bij uw [!DNL Admin] , maar het formulier wordt vernieuwd en u kunt zich niet aanmelden. Dit komt omdat de [!DNL Admin] Grootte sessie is overschreden.

## Betrokken versies

* Adobe Commerce op locatie, [alle ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Probleem

U kunt zich niet aanmelden bij de [!DNL Admin], omdat het formulier steeds opnieuw wordt geladen.

## Oorzaak

De maximaal toegestane sessiegrootte wordt overschreden.

## Oplossing

Controleer de `var/log/support_report.log` bestand voor fouten als deze:

*[2023-07-13T04:26:9.792060+00:00] report.WARNING: De sessiegrootte van 260572 overschrijdt de toegestane sessiegrootte van maximaal 256000. [] []
[2023-07-13T04:26:17.056714+00:00] report.WARNING: De sessiegrootte van 260570 overschrijdt de toegestane sessiegrootte van maximaal 256000. [][]*

Als u deze fouten ziet, zou de oplossing zijn:

<u>Adobe Commerce ter plaatse</u>:
1. Verhoog de **[!UICONTROL Max Session Size in Admin]** waarde uit de achtergrondconfiguratie. Ga hiervoor naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. Stel de waarde in op *500000* of hoger. Afhankelijk van de bestaande maximale grootte die in de fout wordt vermeld, kunt u ook de waarde instellen op *0* waardoor de limiet voor de sessiegrootte wordt verwijderd.

<u>Adobe Commerce over cloudinfrastructuur</u>:

(Deze instelling is alleen toegankelijk in het dialoogvenster [!DNL Admin] wanneer de implementatie-/bewerkingsmodus standaard of ontwikkelaar is. In de cloud-omgeving is echter alleen de implementatiemodus Productie toegestaan.)

Om deze waarde te verhogen, stel dit bevel in de terminal (SSH) in werking:

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

U kunt instellen op hoger dan *500000* afhankelijk van de bestaande maximale grootte die in de fout wordt vermeld en u kunt de waarde ook instellen op *0* om de limiet voor de sessiegrootte te verwijderen.

## Verwante lezing

* [Sessieformaat](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions) in Admin Systems Guide.
* [Bewerkingsmodus](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode) in de Guide Configuratie.
* [Beveiligde verbindingen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) in de Commerce on Cloud Infrastructure Guide.
