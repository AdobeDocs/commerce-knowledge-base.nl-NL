---
title: "Adobe Commerce 2.4.2-p1: factuur met een onjuiste waarde"
description: In dit artikel wordt een bekende Adobe Commerce 2.4.2-p1-uitgave beschreven waarbij een factuuropmerking met een onjuiste waarde wordt gegenereerd wanneer de klantengroep tijdens het maken van de order wordt gewijzigd. Dit probleem is opgelost in versie 2.4.3.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Adobe Commerce 2.4.2-p1: factuur met een onjuiste waarde

In dit artikel wordt een bekende Adobe Commerce 2.4.2-p1-uitgave beschreven waarbij een factuuropmerking met een onjuiste waarde wordt gegenereerd wanneer de klantengroep tijdens het maken van de order wordt gewijzigd. Dit probleem is opgelost in versie 2.4.3.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.2-p1
* Adobe Commerce op cloudinfrastructuur 2.4.2-p1

## Probleem

Wanneer de klantengroep op het tijdstip van het aanmaken van de order wordt gewijzigd, wordt de factuur met een onjuiste factuurverklaring gegenereerd.

<u>Stappen om te reproduceren</u>:

1. Een **Klantenaccount testen** en voeg het toe aan **Retail Customer Group**.
1. Een **Nieuwe volgorde** voor de testklant, voeg **Product** en **Adres**.
1. Selecteren **Verzendmethode**.
1. In de **Accountinformatie** sectie, klantgroep wijzigen vanuit **Detailhandelaar** tot **Overheid**.
1. Klikken **Opdracht plaatsen**.
1. Klikken **Factuur** > **Factuur verzenden**.

<u>Verwachte resultaten</u>:

De volgende opmerking moet worden opgenomen onder de **Notities voor deze volgorde**  sectie: &quot;De factuur voor hoekpunt is verzonden. Bedrag: $0.00.&quot;

<u>Werkelijke resultaten</u>:

De volgende opmerking wordt weergegeven onder de **Notities voor deze volgorde** sectie: &quot;De factuur voor hoekpunt is verzonden. Bedrag: $ 3,23.&quot;

## Oplossing

Dit probleem is opgelost in versie 2.4.3.
