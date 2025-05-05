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

Dit gebeurt wanneer de Variabelen niet worden bijgewerkt nadat een nieuw domein is toegevoegd of wanneer de verkeerde [!DNL Fastly] -service in de omgeving is geconfigureerd.

## Oplossing

1. Als het domein binnen het zelfde milieu opnieuw richt, zorg ervoor dat u de [ Variabelen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=nl-NL#modify-variables) hebt gevormd.
1. Als het domein naar een andere omgeving omleidt, controleert u of u de juiste [!DNL Fastly] -service hebt geconfigureerd door de volgende opdracht uit te voeren: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>U kunt de [!DNL Fastly] API-referenties vinden door u aan te melden bij elke omgeving (Staging/Productie) en het `/mnt/shared/fastly_tokens.txt` -bestand te controleren. Voor meer informatie, zie [  [!DNL Fastly]  de diensten ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=nl-NL) in Commerce op de Gids van de Infrastructuur van de Wolk vormen.

Als beide bovenstaande configuraties correct zijn, dient u een ondersteuningsticket in.

## Gerelateerde lezing

* [ Checklist voor vestiging een nieuw domein ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html?lang=nl-NL) in onze basis van de steunkennis.
