---
title: Fout bij valideren van snelle referenties
description: Dit artikel biedt een oplossing voor het probleem waarbij een gebruiker een fout krijgt bij het valideren van de Fastly-referenties.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 831a928dbe8fd6b37f3fe9ad5dc35ee80e11a578
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
* Uitbreiding of technologie (snelweg, New Relic, enz.) versie snel

## Oplossing

1. Controleer of u de juiste Fastly Service ID en API-token hebt en probeer opnieuw te valideren. Zie voor gedetailleerde instructies [Test de snelreferenties](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#test-the-fastly-credentials) in onze ontwikkelaarsdocumentatie.
1. Als het verifiëren van de geloofsbrieven ontbreekt, stel het volgende krullbevel in werking om de status van de dienst te bevestigen:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Als de bovenstaande opdracht een soortgelijke fout retourneert: *{&quot;msg&quot;:&quot;Token $TOKEN is verlopen op 2021-09-28T02:03:37Z&quot;}*, dient u een ondersteuningsticket in om een nieuw API-token aan te vragen.

   Als u wilt leren hoe u een ondersteuningsticket kunt verzenden, raadpleegt u [Adobe Commerce Help Center - Gebruikershandleiding > ONDERSTEUNINGSTICKETS](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) in onze kennisbasis voor ondersteuning.

   >[!NOTE]
   >
   >U kunt nooit wachtwoorden of geldige/actieve API-tokens rechtstreeks in het ticket delen, omdat we de huidige token moeten intrekken en een nieuwe token moeten genereren om beveiligingsredenen.

1. Als het bevel niet de fout terugkeert, zorg ervoor dat u de nieuwste versie van uitvoert [!DNL Fastly] extensie. Als u een oudere versie gebruikt dan versie 1.2.203, moet u eerst klikken op **[!UICONTROL Save Config]** voordat u de referenties kunt testen.

## Verwante lezingen in onze ontwikkelaarsdocumentatie:

* [Cloud voor Adobe Commerce > Fastly > Fastly service account and credentials](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html#fastly-service-account-and-credentials)

* [Cloud voor Adobe Commerce > Snel instellen > Snelle referenties testen](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#test-the-fastly-credentials)
