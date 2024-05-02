---
title: Magento Order Management System (OMS) for Adobe Commerce processing error
description: Dit artikel verstrekt een oplossing voor de kwestie wanneer u een "getMode ()"fout in CLI krijgt die ` bin/magento ruimten in werking stelt:messages:proces" in het systeem voor Magento Orders Management (OMS) voor Adobe Commerce.
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Magento Order Management System (OMS) for Adobe Commerce processing error

Dit artikel biedt een oplossing voor het probleem wanneer u een `getMode()` fout in CLI die loopt `bin/magento oms:messages:process` in het Magento Order Management System (OMS) for Adobe Commerce.

## Betrokken producten en versies

Deze fout treedt op wanneer u MCOM-connectorversie 3.1.1 en 3.2.0 gebruikt. Het wordt opgelost in Schakelaar MCOM 3.3.0. Dit is niet specifiek voor een MDC- of MOM-versie.

## Probleem

Wanneer het runnen van het volgende bevel in CLI:

`bin/magento oms:messages:process`

Een foutenmelding gelijkend op het volgende wordt uitgevoerd in CLI:

```
<project-id>@<project-id>:~$ php bin/magento oms:messages:process

Processing messages...

PHP Fatal error:Uncaught Error: Call to a member function getMode()
on null in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php:64

Stack trace:

  #0 [internal function]: Magento\InventoryMessageBus\Handler\OnAggregateStockUpdatedSubscriber->onUpdated(Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #1 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(81):
  call_user_func(Array, Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #2 [internal function]: Magento\ServiceBus\Message\SingleMessageProcessor->Magento\ServiceBus\Message\\{closure}(Array)

  #3 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(86):
  array_map(Object(Closure), Array)

  #4 /app/<project-id>/vendor/magento/module-service-bus/Message/Processor.php(110):
  Magento\ServiceBus\Message\SingleMessageProcessor->process(Object(Magento\CommonMessageBus\Message\Message))

  #5 /app/t in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php
  on line 64
```

## Oorzaak

Dit komt voor wanneer de Schakelaar probeert te verwerken `magento.inventory.source_management` berichten. De schakelaar probeert deze berichten te verwerken alsof zij a `magento.inventory.source_stock_management.update` een bericht waarvoor wel een moduswaarde is vereist. Omdat er geen modus is in het dialoogvenster `magento.inventory.source_mangement` -berichten, treedt de fout op.

## Oplossing

Om het probleem op te lossen, stel de volgende SQL verklaring in CLI in werking die alle verslagen in CLI schrapt `mcom_api_messages` tabel:

`delete from mcom_api_messages;`

## Verwante lezing

Zie OMS Docs [Zelfstudie OMS Connector](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/).
