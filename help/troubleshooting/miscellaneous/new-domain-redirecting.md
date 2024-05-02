---
title: Nieuw domein wordt omgeleid naar standaarddomein
description: Dit artikel biedt een oplossing voor het probleem waarbij het nieuwe domein wordt omgeleid naar het standaarddomein in de bestaande of andere omgeving.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Nieuw domein wordt omgeleid naar standaarddomein

Dit artikel biedt een oplossing voor het probleem waarbij het nieuwe domein wordt omgeleid naar het standaarddomein in de bestaande of andere omgeving.

## Betrokken producten en versies

* Adobe Commerce op cloud Pro-infrastructuur (alle versies)

## Probleem

Het nieuwe domein wordt omgeleid naar het standaarddomein in de huidige omgeving of het standaarddomein van een andere omgeving.

## Oorzaak

Dit gebeurt wanneer de variabelen niet worden bijgewerkt na het toevoegen van een nieuw domein of het verkeerde domein. [!DNL Fastly] de dienst is gevormd in het milieu.

## Oplossing

1. Als het domein binnen het zelfde milieu opnieuw richt, zorg ervoor dat u hebt gevormd [Variabelen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables).
1. Als het domein aan een ander milieu opnieuw richt, controleer of u het correcte hebt gevormd [!DNL Fastly] de dienst door het volgende bevel in werking te stellen: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>U kunt de [!DNL Fastly] API-referenties door u aan te melden bij elke omgeving (Staging/Productie) en de `/mnt/shared/fastly_tokens.txt` bestand. Zie voor meer informatie [vormen [!DNL Fastly] diensten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in de Commerce on Cloud Infrastructure Guide.

Als beide bovenstaande configuraties correct zijn, dient u een ondersteuningsticket in.

## Gerelateerde lezing

* [Controlelijst voor het instellen van een nieuw domein](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html) in onze kennisbasis voor ondersteuning.
