---
title: Verbeteringsverzoek integratieomgeving - Pro en Starter
description: Als u een Adobe Commerce bent op het gebied van cloudinfrastructuur Pro en momenteel de standaardomgevingen voor integratie gebruikt, of als u een Adobe Commerce bent op het gebied van de architectuur van de starterarchitectuur van de cloudinfrastructuur en momenteel de standaardgrootteklasse Staging Environment gebruikt en meer stroom wilt, kunt u een upgrade aanvragen naar de Enhanced Integration-omgevingen, die ongeveer vier keer de prestaties leveren. In dit artikel worden instructies voor Pro-klanten gescheiden van Starter-klanten.
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# Verbeteringsverzoek integratieomgeving - Pro en Starter

Als u een Adobe Commerce bent op het gebied van cloudinfrastructuur Pro en momenteel de standaardomgevingen voor integratie gebruikt, of als u een Adobe Commerce bent op het gebied van de architectuur van de starterarchitectuur van de cloudinfrastructuur en momenteel de standaardgrootteklasse Staging Environment gebruikt en meer stroom wilt, kunt u een upgrade aanvragen naar de Enhanced Integration-omgevingen, die ongeveer vier keer de prestaties leveren. In dit artikel worden instructies voor Pro-klanten gescheiden van Starter-klanten.

>[!NOTE]
>
> De bevordering aan Verbeterde Integratie kan niet alle prestatieskwesties behandelen aangezien het van de totale middelvereisten van uw installatie, met inbegrip van derdesintegraties of aanpassingen zou afhangen.
>
> U moet ook ervoor zorgen dat u de beste praktijken voor beste prestaties in het integratiemilieu volgt, en zelfs dat niet een eind-al oplossing kan zijn. Verwijs naar de volgende documentatie voor begeleiding: [ Pro architectuur ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment) en [ architectuur van de Aanzet ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment) in Commerce op de Gids van de Infrastructuur van de Wolk.

## Pro

1. Als u op Pro bent, om te bevorderen, moet u het aantal takken van de Integratie aan twee verminderen (**de belangrijkste tak van de Integratie is inbegrepen in het totaal**). **Nota: Telt niet de primaire tak in dit totaal. De primaire vertakking wordt niet beschouwd als een integratievertakking.** volg de stappen in [ leiden takken met de Console van de Wolk ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) in onze ontwikkelaarsdocumentatie.
1. De handelaar moet [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen die om een Verbetering verzoekt aan Verbeterde Milieu&#39;s van de Integratie, gebruikend de contactreden &quot;*verzoek een verandering van de wolkenconfiguratie*&quot;.
1. Het team van de Techniek van de Klant van de Adobe bevestigt het aantal milieu&#39;s van de Integratie en begint de verandering.
1. De handelaar zal in het kaartje op de hoogte worden gebracht wanneer de verbetering volledig is.
1. De handelaar herstelt de Milieu&#39;s van de Integratie. Volg de stappen in [ een tak ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) in onze ontwikkelaarsdocumentatie samenvoegen. *Nota*: De plaatsing gebeurt automatisch wanneer u in werking stelt: <pre>oorsprong van git-push <branch-name></pre>

De verhoogde prestaties wijzen op een succesvolle verbetering aan Verbeterde Milieu van de Integratie.

**Nota&#39;s**:

* De standaardgrootte en de verbeterde grootte zijn de enige twee beschikbare formaten.
* Alle integratieomgevingen voor een bepaalde winkel zijn even groot - ze kunnen niet afzonderlijk van grootte worden weergegeven.
* Als u meer dan twee van de Verbeterde milieu&#39;s van de Integratie nodig hebt, gelieve uw Team van de Rekening van de Adobe te raadplegen.

## Starter

1. De plannen van de aanzet kunnen geen takken van de Integratie hebben: de verkopers moeten de milieu&#39;s van de Integratie schrappen en slechts het het Opvoeren milieu verlaten. Volg de stappen in [ leiden takken met de Console van de Wolk ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) in onze ontwikkelaarsdocumentatie. Het aantal beschikbare omgevingen wordt beperkt om maximaal één integratieomgeving mogelijk te maken.
1. De handelaar moet [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen die om een Verbetering aan Verbeterde Milieu&#39;s van de Integratie verzoekt, gebruikend de contactreden *&quot;verzoek een verandering van de wolkenconfiguratie&quot;* - **uw het Opvoeren milieu is een genoemd Milieu van de Integratie**.
1. Het team van de Techniek van de Klant van de Adobe bevestigt het aantal milieu&#39;s van de Integratie en begint de verandering.
1. De handelaar zal in het kaartje op de hoogte worden gebracht wanneer de verbetering volledig is.
1. De handelaar herstelt de Milieu&#39;s van de Integratie. Volg de stappen in [ een tak ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) in onze ontwikkelaarsdocumentatie samenvoegen. *Nota*: De plaatsing gebeurt automatisch wanneer u in werking stelt: <pre>oorsprong van git-push <branch-name></pre>

De verhoogde prestaties wijzen op een succesvolle verbetering aan Verbeterde Milieu van de Integratie.

**Nota&#39;s**:

* De standaardgrootte en de verbeterde grootte zijn de enige twee beschikbare formaten.
* Alle integratieomgevingen voor een bepaalde winkel zijn even groot - ze kunnen niet afzonderlijk van grootte worden weergegeven.
* Raadpleeg het accountteam van de Adobe als u integratie-omgevingen nodig hebt die verdergaan met het opslaan.
* Indien de aankoop na 17 september 2020 plaatsvindt, is deze verbetering niet van toepassing vanwege de uitgebreide integratieomgeving.
