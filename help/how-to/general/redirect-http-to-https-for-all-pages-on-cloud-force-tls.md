---
title: HTTP omleiden naar HTTPS voor alle pagina's op Adobe Commerce op cloudinfrastructuur (TLS afdwingen)
description: Activeer de functie **TLS*** van Fastly in Commerce Admin om de globale omleiding van HTTP naar HTTPS voor alle pagina's van uw Adobe Commerce in de opslag van de wolkeninfrastructuur toe te laten.
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# HTTP omleiden naar HTTPS voor alle pagina&#39;s op Adobe Commerce op cloudinfrastructuur (TLS afdwingen)

De sneltoetsen activeren **TLS forceren** in de Commerce Admin-functionaliteit om de algemene omleiding van HTTP naar HTTPS voor alle pagina&#39;s van uw Adobe Commerce in de cloud-infrastructuuropslag mogelijk te maken.

Dit artikel bevat gedetailleerde informatie [stappen](#steps), een kort overzicht van de functie TLS forceren, de desbetreffende versies en koppelingen naar gerelateerde documentatie.

## Stappen {#steps}

### Stap 1: Veilige URL&#39;s configureren {#step-1-configure-secure-urls}

In deze stap, bepalen wij veilige URLs voor de opslag. Als dat al gedaan is, ga naar [Stap 2: TLS forceren inschakelen](#step-2-enable-force-tls).

1. Meld u aan bij de Commerce-beheerder.
1. Navigeren naar **Winkels** > **Configuratie** > **Algemeen** > **Web**.
1. Breid uit **Basis-URL&#39;s (veilig)** sectie.    ![magento-admin_base-urls-secure.png](assets/magento-admin_base-urls-secure.png)
1. In de **Beveiligde basis-URL** in, geeft u de HTTPS-URL van uw winkel op.
1. Stel de **Beveiligde URL&#39;s gebruiken in winkelefront** en de **Beveiligde URL&#39;s gebruiken op Admin** instellingen voor **Ja**.    ![magento-admin_base-urls-secure-settings.png](assets/magento-admin_base-urls-secure-settings.png)
1. Klikken **Configuratie opslaan** in de rechterbovenhoek om wijzigingen toe te passen.

**Verwante documentatie in onze gebruikershandleiding:**   [URL&#39;s opslaan](https://docs.magento.com/m2/ee/user_guide/stores/store-urls.html).

### Stap 2: TLS forceren inschakelen {#step-2-enable-force-tls}

1. Navigeer in Commerce Admin naar **Winkels** > **Configuratie** > **Geavanceerd** > **Systeem**.
1. Breid uit **Volledige paginacache** sectie, dan **Snelle configuratie** vervolgens **Geavanceerde configuratie**.
1. Klik op de knop **TLS forceren** knop.    ![magento-admin_force-tls-button.png](assets/magento-admin_force-tls-button.png)
1. Klik in het dialoogvenster dat wordt weergegeven op **Uploaden**.    ![magento-admin_force-tls-confirm-dialog.png](assets/magento-admin_force-tls-confirmation-dialog.png)
1. Nadat het dialoogvenster is gesloten, controleert u of de huidige status van TLS voor forceren wordt weergegeven als **enabled**.    ![magento-admin_force-tls-enabled.png](assets/magento-admin_force-tls-enabled.png)

**Verwante sneldocumentatie:**   [TLS-handleiding forceren](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md) voor Adobe Commerce 2.

## Info TLS forceren

TLS (Transport Layer Security) is een protocol voor veilige HTTP-verbindingen dat de minder veilige voorganger vervangt, namelijk het SSL-protocol (Secure Socket Layer).

Met de TLS-functionaliteit van Fastly forceert u alle binnenkomende ongecodeerde aanvragen voor uw sitepagina&#39;s naar TLS.

>>
Het werkt door een *301 Permanent verplaatst* reageren op een niet-gecodeerde aanvraag die wordt omgeleid naar het TLS-equivalent. Zo kunt u bijvoorbeeld een verzoek indienen voor *http://www.example.com/foo.jpeg* omleiden naar *https://www.example.com/foo.jpeg*.

[Communicatie beveiligen](https://docs.fastly.com/guides/securing-communications/) (Snelle documentatie)

## Betrokken versies

* **Adobe Commerce op cloudinfrastructuur:**
   * versie: 2.1.4 en hoger
   * plannen: Adobe Commerce on cloud Infrastructure Starter-planarchitectuur en Adobe Commerce on cloud Infrastructure Pro-planarchitectuur (inclusief Pro Legacy)
* **Snel:** 1.2.4.

## Geen veranderingen nodig in routes.yaml

HTTP inschakelen naar HTTPS omleiden **alles** pagina&#39;s van uw winkel, hoeft u de pagina&#39;s niet aan de `routes.yaml` configuratiebestand—Het is voldoende om TLS wereldwijd voor uw gehele winkel te forceren (met Commerce Admin).

## Verwante sneldocumentatie

* [TLS-handleiding forceren voor Adobe Commerce 2](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [TLS-omleiding forceren](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect)
* [Communicatie beveiligen](https://docs.fastly.com/guides/securing-communications/)
