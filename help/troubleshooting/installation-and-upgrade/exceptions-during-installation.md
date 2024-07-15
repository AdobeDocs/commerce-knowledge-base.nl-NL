---
title: Uitzonderingen tijdens installatie
description: Dit artikel verstrekt een mogelijke oplossing voor de kwesties met het installeren van Adobe Commerce gebruikend de Tovenaar van de Opstelling van het Web.
exl-id: f9b8ba2d-c8bd-4020-9e95-7194cc51317c
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Uitzonderingen tijdens installatie

Dit artikel verstrekt een mogelijke oplossing voor de kwesties met het installeren van Adobe Commerce gebruikend de Tovenaar van de Opstelling van het Web.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Probleem

Uitzonderingen worden tijdens de installatie weergegeven. De gebruikers hebben een verscheidenheid van uitzonderingen, met inbegrip van het volgende gemeld:

```bash
Module 'Magento_Indexer':
Running recurring..
[ERROR] exception 'Exception' with message 'Recoverable Error: Argument 1 passed to Magento\Indexer\Model\Config\Data::__construct() must be an instance of Magento\Framework\Indexer\Config\Reader, instance of Magento\Indexer\Model\Config\Reader given, called in /home/magento2_dev/
public_html/generated/code/Magento/Indexer/Model/Config/Data/Interceptor.php on line 14 and defined in /home/magento2_dev/public_html/
app/code/Magento/Indexer/Model/Config/Data.php on line 22' in /home/magento2_dev/public_html/lib/internal/Magento/Framework/App/ErrorHandler.php:67
Stack trace:
#0 /home/magento2_dev/public_html/app/code/Magento/Indexer/Model/Config/Data.php(22): Magento\Framework\App\ErrorHandler->handler(4096,
'Argument 1 pass...', '/home/magento2...', 22, Array)
#1 /home/magento2_dev/public_html/generated/code/Magento/Indexer/Model/Config/Data/Interceptor.php(14): Magento\Indexer\Model\Config\Data->
__construct(Object(Magento\Indexer\Model\Config\Reader), Object(Magento\Framework\App\Cache\Type\Config), Object(Magento\Indexer\Model\Resource\Indexer\State\Collection), 'indexer_config')
#2 /home/magento2_dev/public_html/lib/internal/Magento/Framework/ObjectManager/Factory/AbstractFactory.php(103): Magento\Indexer\Model\Config\Data\Interceptor->__construct(Object(Magento\Indexer\Model\Config\Reader), Object(Magento\Framework\App\Cache\Type\Config),
Object(Magento\Indexer\Model\Resource\Indexer\State\Collection), 'indexer_config')

... more ...
```

## Oplossing

Wis de mappen `<magento_root>/generated/code` en overige mappen onder `var` en `generated` als volgt:

```bash
rm -rf <magento_root>/generated/code/* <magento_root>/generated/metadata/* <magento_root>/var/cache/*
```

Nadat u de directory&#39;s hebt gewist, probeert u de installatie opnieuw.
