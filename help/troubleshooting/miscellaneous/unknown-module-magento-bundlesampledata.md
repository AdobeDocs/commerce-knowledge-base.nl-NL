---
title: Onbekend module Magento_BundleSampleData
description: Dit artikel bevat een oplossing voor de onbekende modulefout tijdens de installatie van Adobe Commerce.
exl-id: c927bc8f-d70b-4305-87c1-223001212555
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Onbekend module Magento_BundleSampleData

Dit artikel bevat een oplossing voor de onbekende modulefout tijdens de installatie van Adobe Commerce.

## Probleem {#details}

Tijdens de installatie wordt een bericht weergegeven dat lijkt op het volgende:

```text
[ERROR] exception 'LogicException' with message 'Unknown module in the requested list: 'Magento_BundleSampleData''
```

## Oplossing {#solution}

Probeer elk van de volgende opties een voor een opnieuw en probeer de installatie opnieuw.

1. Voer de wizard Webinstellingen uit. Modules worden vermeld in  **Geavanceerde moduleconfiguraties**. Om het **Magento\_BundleSampleData** -module, wist de **Magento\_BundleSampleData** checkbox zoals het volgende cijfer toont.

   ![tshoot_bundlesampledata.png](assets/tshoot_bundlesampledata.png)

1. Wis alle browsergeschiedenis en gegevens uit uw webbrowser.
1. Als u Chrome hebt, wist u alle browsergegevens met betrekking tot uw site.  Ga naar **Instellingen** > **Geavanceerde opties** > **Privacy** > **Inhoudsinstellingen** > **Alle cookies en sitegegevens**. Klik in de kolom Site op het adres van uw Adobe Commerce-server en klik op **Alles verwijderen**.
