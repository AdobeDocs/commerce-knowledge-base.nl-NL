---
title: Fout wanneer het bevestigen van de  [!DNL Fastly]  geloofsbrieven
description: Dit artikel verstrekt een oplossing voor de kwestie waar een gebruiker een fout wanneer het bevestigen van de  [!DNL Fastly]  geloofsbrieven krijgt.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 838f0c5d55c29d026dc37a8f7e5214b9880a4353
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Fout bij het valideren van de [!DNL Fastly] -referenties

Dit artikel verklaart hoe te om *Symbolische verlopen* fouten op te lossen die bij het bevestigen van [!DNL Fastly] geloofsbrieven worden ontmoet.

De stappen die in dit artikel worden beschreven, zijn ook van toepassing als u uw [!DNL Fastly] API-token om beveiligingsredenen moet roteren (doorlopen). In deze gevallen dient u een Adobe Commerce Support-ticket in te dienen om een nieuwe [!DNL Fastly] API-token aan te vragen.

## Probleem

* Er treedt een fout op bij het valideren van de [!DNL Fastly] -referenties.
* U vermoedt dat uw [!DNL Fastly] token mogelijk in gevaar is gebracht, bijvoorbeeld als deze onbedoeld werd gedeeld in een ondersteuningsticket of op een openbaar forum werd geplaatst.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden): alle versies
* Versie voor extensie of technologie ([!DNL Fastly], [!DNL New Relic], enz.) [!DNL Fastly]

## Oplossing

1. Controleer of u de juiste service-id en API-token voor [!DNL Fastly] hebt en probeer opnieuw te valideren. Voor gedetailleerde instructie, verwijs naar [&#x200B; Test de  [!DNL Fastly]  geloofsbrieven &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials) in onze ontwikkelaarsdocumentatie.
1. Als het verifiëren van de geloofsbrieven ontbreekt, stel het volgende krullbevel in werking om de status van de dienst te bevestigen:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Als de bovenstaande opdracht een fout retourneert die lijkt op: `{"msg":"Token $TOKEN expired at 2021-09-28T02:03:37Z"}` , verzendt u een ondersteuningsticket om een nieuwe API-token aan te vragen. Nadat u het nieuwe token hebt ontvangen, werkt u de configuratie in uw omgeving bij.

   Leren hoe te om een steunkaartje voor te leggen, verwijs naar [&#x200B; Gids van de Gebruiker van het Centrum van Adobe Commerce > STEUN TICKETS &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) in onze basis van de steunkennis.

   >[!NOTE]
   >
   >U kunt nooit wachtwoorden of geldige/actieve API-tokens rechtstreeks in het ticket delen, omdat we de huidige token moeten intrekken en een nieuwe token moeten genereren om beveiligingsredenen.
   >
   >Adobe Commerce Support heeft toegang tot de tokens, dus u hoeft deze gegevens niet op te nemen in het ticket.

1. Als de opdracht de fout niet retourneert, controleert u of u de nieuwste versie van de extensie [!DNL Fastly] uitvoert. Als u een oudere versie gebruikt dan versie 1.2.203, moet u eerst op **[!UICONTROL Save Config]** klikken voordat u de referenties kunt testen.

## Verwante lezingen in onze ontwikkelaarsdocumentatie:

* [&#x200B; Wolk voor Adobe Commerce >  [!DNL Fastly] >  [!DNL Fastly]  de dienstrekening en geloofsbrieven &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/fastly?lang=en#fastly-service-account-and-credentials)

* [&#x200B; Wolk voor Adobe Commerce > Opstelling  [!DNL Fastly] > Test de  [!DNL Fastly]  geloofsbrieven &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)
