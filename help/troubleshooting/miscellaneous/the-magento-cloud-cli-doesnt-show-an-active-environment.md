---
title: '&grave; Magento-wolk &grave;  [!DNL CLI]  toont geen actief milieu'
description: Dit artikel beschrijft een bekende kwestie van Adobe Commerce waar Magento-wolk &grave;  [!DNL CLI]  (bevel-lijn hulpmiddel) geen actieve milieu toont.
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
source-git-commit: 5eac8bb54e205eff6a96e279295cd12db1009f0a
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# In `Magento-cloud` [!DNL CLI] wordt geen actieve omgeving weergegeven

## Probleem

Er zijn verschillende actieve omgevingen en u probeert te communiceren met een omgeving door een opdracht `Magento-cloud` [!DNL CLI] (opdrachtregelprogramma) uit te voeren. (Bijvoorbeeld: `ssh` , `db:size` , `db:sql` , enz.)
Nochtans, maakt de herinnering om het gewenste milieu te kiezen geen lijst van deze milieu. (Bijvoorbeeld: de integratieomgeving)

```
Enter a number to choose an environment:
Default: master
  [0] integration2 (type: development)
  [1] master (type: development)
  [2] production
  [3] staging
 >
```

## Oorzaak

Het is mogelijk dat de omgeving niet beschikbaar is vanwege een implementatie die bezig is, vastzit of is mislukt.

## Oplossing

U moet de omgeving handmatig opgeven met de markering `e|-environment` .

1. Zoek de lijst met actieve omgevingen en noteer de namen van de omgevingen:

```
$ magento-cloud environment: list |grep "Active\|ID"
Your environments are:

| ID                     | Title            | Status       | Type           |
| Master                 | Master           | Active       | Development    |
|   Production           | Production       | Active       | Production     |
|     Staging            | Staging          | Active       | Staging        |
|       Integration      | Integration      | Active       | Development    |
|          Integration 2 | Integration 2    | Active       | Development    |
```

2.Geef de id van de omgeving op met uw opdracht:

`magento-cloud ssh -e integration`
