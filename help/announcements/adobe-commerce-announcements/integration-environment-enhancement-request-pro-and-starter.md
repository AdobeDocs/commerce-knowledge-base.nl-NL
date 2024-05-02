---
title: Verbeteringsverzoek integratieomgeving - Pro en Starter
description: Als u een Adobe Commerce bent op het gebied van cloudinfrastructuur Pro en momenteel de standaardomgevingen voor integratie gebruikt, of als u een Adobe Commerce bent op het gebied van de architectuur van de starterarchitectuur van de cloudinfrastructuur en momenteel de standaardgrootteklasse Staging Environment gebruikt en meer stroom wilt, kunt u een upgrade aanvragen naar de Enhanced Integration-omgevingen, die ongeveer vier keer de prestaties leveren. In dit artikel worden instructies voor Pro-klanten gescheiden van Starter-klanten.
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: 43be85de953909253900d60488f76a20bac91793
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 0%

---

# Verbeteringsverzoek integratieomgeving - Pro en Starter

Als u een Adobe Commerce bent op het gebied van cloudinfrastructuur Pro en momenteel de standaardomgevingen voor integratie gebruikt, of als u een Adobe Commerce bent op het gebied van de architectuur van de starterarchitectuur van de cloudinfrastructuur en momenteel de standaardgrootteklasse Staging Environment gebruikt en meer stroom wilt, kunt u een upgrade aanvragen naar de Enhanced Integration-omgevingen, die ongeveer vier keer de prestaties leveren. In dit artikel worden instructies voor Pro-klanten gescheiden van Starter-klanten.

## Pro

1. Als u Pro bent, aan verbetering, moet u het aantal takken van de Integratie tot twee verminderen (**de belangrijkste bedrijfstak van de Integratie omvat in het totaal**). **Opmerking: tel de primaire vertakking niet in dit totaal. De primaire vertakking wordt niet beschouwd als een integratievertakking.** Voer de stappen uit in [Vertakkingen beheren met de Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) in onze ontwikkelaarsdocumentatie.
1. De handelaar moet [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om een Verbetering aan Verbeterde milieu&#39;s van de Integratie te verzoeken, gebruikend de contactreden &quot;*Een wijziging in de cloudconfiguratie aanvragen*&quot;.
1. Het team van de Techniek van de Klant van de Adobe bevestigt het aantal milieu&#39;s van de Integratie en begint de verandering.
1. De handelaar zal in het kaartje op de hoogte worden gebracht wanneer de verbetering volledig is.
1. De handelaar herstelt de Milieu&#39;s van de Integratie. Voer de stappen uit in [Een vertakking samenvoegen](https://devdocs.magento.com/cloud/env/environments-start.html#merge) in onze ontwikkelaarsdocumentatie. *Opmerking*: De plaatsing gebeurt automatisch wanneer u in werking stelt: <pre>oorsprong van git-push <branch-name></pre>

De verhoogde prestaties wijzen op een succesvolle verbetering aan Verbeterde Milieu van de Integratie.

**Notities**:

* De standaardgrootte en de verbeterde grootte zijn de enige twee beschikbare formaten.
* Alle integratieomgevingen voor een bepaalde winkel zijn even groot - ze kunnen niet afzonderlijk van grootte worden weergegeven.
* Als u meer dan twee van de Verbeterde milieu&#39;s van de Integratie nodig hebt, gelieve uw Team van de Rekening van de Adobe te raadplegen.

## Starter

1. De plannen van de aanzet kunnen geen takken van de Integratie hebben: de verkopers moeten de milieu&#39;s van de Integratie schrappen en slechts het het Opvoeren milieu verlaten. Voer de stappen uit in [Vertakkingen beheren met de Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) in onze ontwikkelaarsdocumentatie. Het aantal beschikbare omgevingen wordt beperkt om maximaal één integratieomgeving mogelijk te maken.
1. De handelaar moet [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om een Verbetering aan Verbeterde Milieu&#39;s van de Integratie te verzoeken, gebruikend de contactreden *&quot;Een wijziging in de cloudconfiguratie aanvragen&quot;* -  **uw het Staging milieu is genoemd een Omgeving van de Integratie**.
1. Het team van de Techniek van de Klant van de Adobe bevestigt het aantal milieu&#39;s van de Integratie en begint de verandering.
1. De handelaar zal in het kaartje op de hoogte worden gebracht wanneer de verbetering volledig is.
1. De handelaar herstelt de Milieu&#39;s van de Integratie. Voer de stappen uit in [Een vertakking samenvoegen](https://devdocs.magento.com/cloud/env/environments-start.html#merge) in onze ontwikkelaarsdocumentatie. *Opmerking*: De plaatsing gebeurt automatisch wanneer u in werking stelt: <pre>oorsprong van git-push <branch-name></pre>

De verhoogde prestaties wijzen op een succesvolle verbetering aan Verbeterde Milieu van de Integratie.

**Notities**:

* De standaardgrootte en de verbeterde grootte zijn de enige twee beschikbare formaten.
* Alle integratieomgevingen voor een bepaalde winkel zijn even groot - ze kunnen niet afzonderlijk van grootte worden weergegeven.
* Raadpleeg het accountteam van de Adobe als u integratie-omgevingen nodig hebt die verdergaan met het opslaan.
* Indien de aankoop na 17 september 2020 plaatsvindt, is deze verbetering niet van toepassing vanwege de uitgebreide integratieomgeving.
