---
title: Magento Order Management System (OMS) for Adobe Commerce processing error
description: 'Dit artikel verstrekt een oplossing voor de kwestie wanneer u een "getMode ()"fout in CLI krijgt die ` bin/magento :messages: proces ` in het Systeem van het Magento Order Management (OMS) voor Adobe Commerce in werking stelt.'
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Magento Order Management System (OMS) for Adobe Commerce processing error

Dit artikel biedt een oplossing voor het probleem wanneer u een `getMode()` -fout krijgt in de CLI die `bin/magento oms:messages:process` in het Magento Order Management System (OMS) for Adobe Commerce wordt uitgevoerd.

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

A
Dit komt voor wanneer de Schakelaar probeert om `magento.inventory.source_management` berichten te verwerken. De connector probeert deze berichten te verwerken alsof het een `magento.inventory.source_stock_management.update` -bericht betreft waarvoor wel een moduswaarde is vereist. Omdat de `magento.inventory.source_mangement` -berichten geen modus bevatten, treedt de fout op.

## Oplossing

Voer de volgende [!DNL SQL] -instructie in de CLI uit, die alle records in de `mcom_api_messages` -tabel verwijdert, om het probleem op te lossen:

`delete from mcom_api_messages;`

## Verwante lezing

* OMS Docs [ Zelfstudie van de Opstelling van de Schakelaar OMS ](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/)
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
