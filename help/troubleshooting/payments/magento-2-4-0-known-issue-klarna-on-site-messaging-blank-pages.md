---
title: 'Bekende uitgave van Adobe Commerce 2.4.0: blanco pagina''s voor onsite berichten van Klarna'
description: In dit artikel wordt een bekende Adobe Commerce 2.4.0-uitgave met de betaalmethode Klarna beschreven. Als u een onsite berichtgeving van Klarna inschakelt zonder een ontwerpthema op te geven, worden productpagina's niet correct weergegeven op de winkel (productpagina's worden leeg weergegeven).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Bekende uitgave van Adobe Commerce 2.4.0: Klarna On-Site Messaging-blanco pagina&#39;s

In dit artikel wordt een bekende Adobe Commerce 2.4.0-uitgave met de betaalmethode Klarna beschreven. Als u een onsite berichtgeving van Klarna inschakelt zonder een ontwerpthema op te geven, worden productpagina&#39;s niet correct weergegeven op de winkel (productpagina&#39;s worden leeg weergegeven).

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

<u> Eerste vereisten:</u> de betalingsmethode van Klarna wordt toegelaten.

<u> Stappen om te reproduceren:</u>

1. In Commerce Admin, ga **>** Configuratie **>** Verkoop **>** de Methoden van de Betaling **>** Klarna **>** het Overseinen van Klarna On-Site **.**
1. Plaats **laat** toe *ja*.
1. Verlaat het **thema van het Ontwerp** gebiedsspatie.
1. Sparen configuratie door **te klikken sparen Config**.
1. Ga naar de winkel en ga naar een willekeurige productpagina.

<u> Verwacht resultaat:</u>

De pagina wordt geladen met het standaardontwerpthema dat is toegepast voor het on-site berichtenverkeer van Klarna.

<u> Ware resultaat:</u>

Er wordt een lege pagina weergegeven.

## Oplossing

Als het toelaten van het Klarna onsite overseinen, zorg altijd ervoor dat het **het thema** gebied van het Ontwerp niet leeg is.
