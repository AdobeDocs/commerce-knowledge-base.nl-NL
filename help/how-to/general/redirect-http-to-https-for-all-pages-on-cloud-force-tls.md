---
title: HTTP omleiden naar HTTPS voor alle pagina's op Adobe Commerce op cloudinfrastructuur (TLS afdwingen)
description: Activeer de functie **TLS*** van Fastly in Commerce Admin om de globale omleiding van HTTP naar HTTPS voor alle pagina's van uw Adobe Commerce in de opslag van de wolkeninfrastructuur toe te laten.
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# HTTP omleiden naar HTTPS voor alle pagina&#39;s op Adobe Commerce op cloudinfrastructuur (TLS afdwingen)

Activeer de {**functionaliteit 0} van TLS van de Fastly &lbrace;in Commerce Admin om globale HTTP aan HTTPS toe te laten voor alle pagina&#39;s van uw Adobe Commerce op de opslag van de wolkeninfrastructuur opnieuw richten.**

Dit artikel verstrekt gedetailleerde [ stappen ](#steps), een snel overzicht van de eigenschap van de Kracht TLS, beïnvloede versies, en verbindingen aan verwante documentatie.

## Stappen {#steps}

### Stap 1: Veilige URL&#39;s configureren {#step-1-configure-secure-urls}

In deze stap, bepalen wij veilige URLs voor de opslag. Als dat reeds wordt gedaan, ga naar [ Stap 2: laat Ts van de Macht ](#step-2-enable-force-tls) toe.

1. Meld u aan bij de Commerce-beheerder.
1. Navigeer aan **Opslag** > **Configuratie** > **Algemeen** > **Web**.
1. Breid **Basis URLs (Veilig) uit** sectie.    ![ magento-admin_base-urls-secure.png ](assets/magento-admin_base-urls-secure.png)
1. Op het **Veilige gebied URL van de Basis**, specificeer HTTPS URL van uw opslag.
1. Plaats het **Gebruik Veilige URLs op Storefront** en het **Gebruik Veilige URLs op Admin** montages aan **ja**.    ![ magento-admin_base-urls-secure-settings.png ](assets/magento-admin_base-urls-secure-settings.png)
1. Klik **sparen config** in de hoger-juiste hoek om veranderingen toe te passen.

**Verwante documentatie in onze gebruikersgids:**   [ opslag URLs ](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/site-store/store-urls).

### Stap 2: TLS forceren inschakelen {#step-2-enable-force-tls}

1. In Commerce Admin, navigeer aan **Opslag** > **Configuratie** > **Geavanceerd** > **Systeem**.
1. Breid de **Volledige sectie van het Geheime voorgeheugen van de Pagina** uit, toen **Snelle Configuratie**, toen **Geavanceerde Configuratie**.
1. Klik de **knoop van TLS van de Dwangmacht**.    ![ magento-admin_force-tls-button.png ](assets/magento-admin_force-tls-button.png)
1. In de dialoog die verschijnt, klik **uploadt**.    ![ magento-admin_force-tls-bevestiging-dialog.png ](assets/magento-admin_force-tls-confirmation-dialog.png)
1. Nadat de dialoog sluit, zorg ervoor de huidige staat van Ts van de Macht als **toegelaten** wordt getoond.    ![ magento-admin_force-tls-enabled.png ](assets/magento-admin_force-tls-enabled.png)

**Verwante Snelle documentatie:**   [ de gids van TLS van de Dwinging ](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md) voor Adobe Commerce 2.

## Info TLS forceren

TLS (Transport Layer Security) is een protocol voor veilige HTTP-verbindingen dat de minder veilige voorganger vervangt, namelijk het SSL-protocol (Secure Socket Layer).

Met de TLS-functionaliteit van Fastly forceert u alle binnenkomende ongecodeerde aanvragen voor uw sitepagina&#39;s naar TLS.

&#x200B;>>
Het werkt door a *301 terug te keren die permanent* wordt bewogen reactie op om het even welk niet gecodeerd verzoek, dat aan het equivalent TLS opnieuw richt. Bijvoorbeeld, die een verzoek om *http://www.example.com/foo.jpeg* maken zou aan *https://www.example.com/foo.jpeg* opnieuw richten.

[ het Beveiligen van mededelingen ](https://docs.fastly.com/guides/securing-communications/) (Snelle documentatie)

## Betrokken versies

* **Adobe Commerce op wolkeninfrastructuur:**
   * versie: 2.1.4 en hoger
   * plannen: Adobe Commerce on cloud Infrastructure Starter-planarchitectuur en Adobe Commerce on cloud Infrastructure Pro-planarchitectuur (inclusief Pro Legacy)
* **snel:** 1.2.4

## Geen veranderingen nodig in routes.yaml

Om HTTP aan HTTPS toe te laten richt zich op **alle** pagina&#39;s van uw opslag, moet u niet de pagina&#39;s aan `routes.yaml` configuratiedossier-toelatend TLS van de Kracht globaal voor uw volledige opslag (gebruikend Commerce Admin) toevoegen is genoeg.

## Verwante sneldocumentatie

* [ de gids van TLS van de Kracht voor Adobe Commerce 2 ](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [ die een omleiding van TLS ](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect) dwingen
* [ het Beveiligen van mededelingen ](https://docs.fastly.com/guides/securing-communications/)
