---
title: 'Uitgave Adobe Commerce 2.4.1: Amazon-account kan niet worden gewijzigd in Chrome'
description: In dit artikel wordt een bekende Adobe Commerce 2.4.1-kwestie beschreven waarbij klanten zich aanmelden bij eerder gebruikte Amazon-accounts in plaats van te worden voorgesteld zich aan te melden wanneer ze Amazon Pay gebruiken tijdens het afrekenen.
exl-id: 8acffe99-b3ec-4b45-9434-61b66e963838
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Uitgave Adobe Commerce 2.4.1: Amazon-account kan niet worden gewijzigd in Chrome

In dit artikel wordt een bekende Adobe Commerce 2.4.1-kwestie beschreven waarbij klanten zich aanmelden bij eerder gebruikte Amazon-accounts in plaats van te worden voorgesteld zich aan te melden wanneer ze Amazon Pay gebruiken tijdens het afrekenen.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.1
* Adobe Commerce over wolkeninfrastructuur 2.4.1

## Probleem

Klanten worden aangemeld bij de eerder gebruikte Amazon-accounts in plaats van te worden voorgesteld zich aan te melden wanneer ze Amazon Pay gebruiken tijdens het afrekenen.

<u> Stappen om te reproduceren:</u>

1. Voeg in de winkel een willekeurig artikel toe aan het winkelwagentje en ga verder met uitchecken door de gast.
1. Klik de **Pay van Amazon** knoop. Amazon.com. verschijnt een pop-upvenster.
1. Meld u aan bij de Amazon-account.
1. Selecteer een adres en klik **daarna**.
1. Selecteer de betalingsmethode.
1. Klik **orde van de Plaats**.
1. Ga terug naar de homepage en meld u aan bij de winkelaccount.
1. Voeg nog een item aan het winkelwagentje toe en ga door met het afrekenen.
1. Klik de **Pay van Amazon** knoop.

<u> Ware resultaat:</u>

Je wordt automatisch aangemeld bij de eerder gebruikte (Stap 3) Amazon account.

<u> Verwacht resultaat:</u>

Amazon.com. verschijnt een pop-upvenster met de aanmelding en u kunt zich aanmelden of een nieuwe account maken voor Amazon Pay.

## Oorzaak

Het probleem kan zich voordoen in een van de volgende situaties:

* Wanneer de waarde van `SameSite` cookie `LAX` is, wordt het cookie niet verzonden als onderdeel van aanroepen van derden.
* De functie voor het blokkeren van Mozilla Firefox-inhoud voorkomt dat derden de activiteiten van browsergebruikers kunnen bijhouden door het gebruik van scripts en opslagmechanismen op de client te blokkeren. Firefox gebruikt een externe leverancier, Disconnect.me, om een lijst van het volgen plaatsen te verstrekken die moeten worden geblokkeerd. Amazon Pay gebruikt een iframe op een website van derden om een toegangstoken te retourneren na aanmelden en de widget Adres en portemonnee te renderen. Met de functie voor het blokkeren van inhoud worden aanvragen voor iFrame voor laden in Amazon Pay beschouwd als aanvragen voor het bijhouden van gegevens door derden en worden deze geblokkeerd. Hierdoor kan de koper niet doorgaan met afrekenen.
* Elke situatie waarbij cookies van derden of JS expliciet door de browser worden geblokkeerd.

## Oplossing

Zorg ervoor dat Amazon Pay iframe-aanvragen niet door browsers worden geblokkeerd.
