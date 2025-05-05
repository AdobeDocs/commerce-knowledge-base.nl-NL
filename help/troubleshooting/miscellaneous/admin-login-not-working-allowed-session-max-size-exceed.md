---
title: '[!UICONTROL Admin] aanmelden werkt niet - toegestane sessiegrootte is overschreden'
description: Los het probleem op wanneer u zich probeert aan te melden bij het deelvenster [!UICONTROL Admin] en het formulier wordt vernieuwd en u zich niet kunt aanmelden.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: fe4a48581bdfe24da5082b69fb26a8032bd77334
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# [!UICONTROL Admin] aanmelden werkt niet - toegestane sessiegrootte is overschreden

Dit artikel bevat een oplossing voor het aanmelden in het deelvenster [!UICONTROL Admin] , maar het formulier wordt vernieuwd en u kunt zich niet aanmelden, of u voert bepaalde handelingen uit in het deelvenster [!UICONTROL Admin] en wordt automatisch afgemeld.
Dit wordt veroorzaakt doordat [!UICONTROL Admin] [!UICONTROL Session Size] is overschreden.

## Betrokken versies

* Adobe Commerce op-gebouw, [ alle gesteunde versies ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce op wolkeninfrastructuur, [ alle gesteunde versies ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Probleem

U ervaart een van de volgende symptomen op de [!UICONTROL Admin] :

1. U kunt zich niet aanmelden bij de [!UICONTROL Admin] omdat het formulier steeds opnieuw wordt geladen.
1. U wordt automatisch afgemeld wanneer u probeert om een actie uit te voeren.

## Oorzaak

De maximaal toegestane sessiegrootte wordt overschreden.

## Oplossing

Controleer het `var/log/support_report.log` -bestand op fouten zoals deze:

*[2023-07-13T04 :26: 09.792060+00:00 ] report.WAARSCHUWING: De grootte van de zitting van 260572 overtrof toegestane zittingsmaximum grootte van 256000. [] []
[ 2023-07-13T04 :26: 17.056714+00:00 ] report.WAARSCHUWING: De grootte van de zitting van 260570 overtrof toegestane zittingsmaximum grootte van 25600. [][]*

Als u deze fouten ziet, zou de oplossing zijn:

<u> Adobe Commerce op-gebouw </u>:
1. Verhoog de waarde **[!UICONTROL Max Session Size in Admin]** van de achtergrondconfiguratie. Ga hiertoe naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]** .
1. Plaats de waarde aan *500000* of hoger. Afhankelijk van de bestaande die maximumgrootte in de fout wordt gemeld - u kon de waarde aan *ook plaatsen 0* die de grens van de zittingsgrootte zal verwijderen.

<u> Adobe Commerce op wolkeninfrastructuur </u>:

(Dit het plaatsen is slechts toegankelijk op [!UICONTROL Admin] wanneer de plaatsing/verrichtingswijze *gebrek* of *ontwikkelaar* is. In de cloudomgeving is echter alleen de implementatiemodus Productie toegestaan.)

Om deze waarde te verhogen, stel dit bevel in de terminal (SSH) in werking:

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

U kunt aan hoger plaatsen dan *500000* afhankelijk van de bestaande max. grootte die in de fout wordt gemeld en u kunt de waarde aan *ook plaatsen 0* om de grens van de zittingsgrootte te verwijderen.

## Verwante lezing

* [ grootte van de Zitting ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/security/security-session-management#admin-sessions) in de Gids van Systemen Admin
* [ wijze van de Verrichting ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/set-mode) in de Gids van de Configuratie
* [ Veilige verbindingen ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/secure-connections) in Commerce op de Gids van de Infrastructuur van de Wolk
