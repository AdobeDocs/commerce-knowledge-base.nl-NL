---
title: Fout na aanmelden bij Commerce Admin
description: Dit artikel biedt een oplossing voor het probleem waarbij een foutbericht wordt weergegeven dat de aangevraagde URL niet op deze server is gevonden.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Fout na aanmelden bij Commerce Admin

Dit artikel biedt een oplossing voor het probleem waarbij een foutbericht wordt weergegeven dat de aangevraagde URL niet op deze server is gevonden.

## Details

De gevraagde URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ is niet gevonden op deze server.

Let op het gebrek aan een slash tussen `magento2` en `index.php` in de URL.

## Oplossing

De basis-URL is onjuist. De basis-URL moet:

* Beginnen met `http://` of `https://`
* Eindigen met een schuine streep ( `/` )
* Het hoofdlettergebruik van de `web/unsecure/base_url` -record in de `core_config_data` -databasetabel

Voer de installatie opnieuw uit met een geldige waarde.
