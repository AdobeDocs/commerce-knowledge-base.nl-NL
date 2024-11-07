---
title: Fout bij valideren van snelle referenties
description: Dit artikel biedt een oplossing voor het probleem waarbij een gebruiker een fout krijgt bij het valideren van de Fastly-referenties.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Fout bij valideren van snelle referenties

Dit artikel biedt een oplossing voor het probleem waarbij een gebruiker een fout krijgt bij het valideren van de Fastly-referenties.

## Probleem

De gebruiker krijgt een fout wanneer het bevestigen van de Snelle geloofsbrieven.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden): alle versies
* Versie van extensie of technologie (Fastly, New Relic, enz.) Snel

## Oplossing

1. Controleer of u de juiste Fastly Service ID en API-token hebt en probeer opnieuw te valideren. Voor gedetailleerde instructie, verwijs naar [ Test de Snelle geloofsbrieven ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials) in onze ontwikkelaarsdocumentatie.
1. Als het verifiëren van de geloofsbrieven ontbreekt, stel het volgende krullbevel in werking om de status van de dienst te bevestigen:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Als het bovengenoemde bevel een fout gelijkend op terugkeert: *{&quot;msg&quot;:&quot;Symbolische $TOKEN verliep bij 2021-09-28T02 :03: 37Z&quot;}*, leg een steunkaartje voor om een nieuw API teken te verzoeken.

   Leren hoe te om een steunkaartje voor te leggen, verwijs naar [ Gids van de Gebruiker van het Centrum van Adobe Commerce > STEUN TICKETS ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) in onze basis van de steunkennis.

   >[!NOTE]
   >
   >U kunt nooit wachtwoorden of geldige/actieve API-tokens rechtstreeks in het ticket delen, omdat we de huidige token moeten intrekken en een nieuwe token moeten genereren om beveiligingsredenen.

1. Als de opdracht de fout niet retourneert, controleert u of u de nieuwste versie van de extensie [!DNL Fastly] uitvoert. Als u een oudere versie gebruikt dan versie 1.2.203, moet u eerst op **[!UICONTROL Save Config]** klikken voordat u de referenties kunt testen.

## Verwante lezingen in onze ontwikkelaarsdocumentatie:

* [ Cloud voor Adobe Commerce > Snelst > de dienstrekening en geloofsbrieven van de Snelheid ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly#fastly-service-account-and-credentials)

* [ Wolk voor Adobe Commerce > Opstelling Fastly > Test de Snelle geloofsbrieven ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials)
