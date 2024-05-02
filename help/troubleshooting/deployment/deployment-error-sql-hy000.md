---
title: 'Implementatiefout: SQLSTATE[HY000]'
description: Dit artikel biedt een oplossing voor het probleem waarbij de implementatie mislukt als gevolg van de SQLSTATE[HY000]-fout.
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Implementatiefout: SQLSTATE[HY000]

Dit artikel biedt een oplossing voor het probleem waarbij de implementatie mislukt door de SQLSTATE[HY000] fout.

## Betrokken producten en versies

* Adobe Commerce [alle implementatiemethoden](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

Er treedt een SQLSTATE-fout op tijdens de implementatie.

```sql
Updating modules:
SQLSTATE[HY000]: General error: 23 Out of resources when opening file '/tmp/#sql_565c_0.MAD' (Errcode: 24 "Too many open files"),
```

## Oorzaak

Draaien tijdens implementatie.

## Oplossing

Als u het probleem wilt verhelpen, voorkomt u dat het programma wordt uitgevoerd door de opdrachtregel te openen en de volgende opdracht uit te voeren:
`./vendor/bin/ece-tools cron:disable`.
