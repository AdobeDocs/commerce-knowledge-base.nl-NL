---
title: 'Adobe Commerce 2.4.2-p1: factuur met een onjuiste waarde'
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

<u> Stappen om </u> te reproduceren:

1. Creeer de Rekening van de Klant van de a **Test** en voeg het aan de **DetailhandelGroep van de Klant** toe.
1. Creeer a **Nieuwe Orde** voor de testklant, voeg **Product** en **Adres** toe.
1. Selecteer **Verzendmethode**.
1. In de **sectie van de Informatie van de Rekening**, de groep van de veranderingsklant van **Detailhandelaar** aan **Regering**.
1. Klik **de Orde van de Plaats**.
1. Klik **Factuur** > **voorleggen Factuur**.

<u> Verwachte resultaten </u>:

De volgende nota zou onder de **Nota&#39;s voor deze orde** sectie moeten verschijnen: &quot;De Rekening van de top die met succes wordt verzonden. Bedrag: $0.00.&quot;

<u> Ware resultaten </u>:

De volgende nota verschijnt onder de **Nota&#39;s voor deze orde** sectie: &quot;De Rekening van de top die met succes wordt verzonden. Bedrag: $ 3,23.&quot;

## Oplossing

Dit probleem is opgelost in versie 2.4.3.
