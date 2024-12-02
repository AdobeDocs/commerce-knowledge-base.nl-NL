---
title: 'Bekende Adobe Commerce 2.4.1-probleem: fout bij afhandeling met PayPal-Braintree'
description: In dit artikel wordt een bekende Adobe Commerce 2.4.1-kwestie beschreven, waarbij een foutbericht verschijnt en verdwijnt in de afhandelingsstap Factureren als betaling via PayPal-Braintree wordt gebruikt en meerdere adressen voor verzending zijn geselecteerd.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Bekende Adobe Commerce 2.4.1-probleem: fout bij afhandeling met PayPal-Braintree

In dit artikel wordt een bekende Adobe Commerce 2.4.1-kwestie beschreven, waarbij een foutbericht verschijnt en verdwijnt in de afhandelingsstap Factureren als betaling via PayPal-Braintree wordt gebruikt en meerdere adressen voor verzending zijn geselecteerd.

## Betrokken producten en versies

* Adobe Commerce over wolkeninfrastructuur 2.4.1
* Adobe Commerce op locatie 2.4.1

## Probleem

Er verschijnt een foutbericht en dit bericht verdwijnt bij de afhandeling van de betalingsmethode als betaling via PayPal-Braintree wordt gebruikt en als de verzending van meerdere adressen is geselecteerd.

<u> Stappen om te reproduceren:</u>

1. Voor de opslag, login als klant (facultatief zou een gastcontrole kunnen zijn, als het in Admin wordt toegelaten).
1. Voeg een product toe aan de kar.
1. Klik om de voorvertoning van het winkelwagentje te openen.
1. Klik **Mening en geef Kar** uit.
1. Voor de pagina van het Kunst, klik **Controle uit met Veelvoudige Adressen**.
1. Klik **gaan naar de Verzendinformatie** en specificeer de adressen.
1. Klik **blijven aan het Factureren Informatie**.
1. Selecteer **Braintree PayPal** en klik de **PayPal** knoop.
1. In het pop-up venster, klik **Akkoord &amp; betaal**.

<u> Verwacht resultaat:</u>

De volgorde wordt zonder fout geplaatst.

<u> Ware resultaat:</u>

De volgorde wordt geplaatst, maar met een fout. De *PayPal Afhandeling kon niet worden geïnitialiseerd. Gelieve te contacteren opslageigenaar*.  fout wordt een seconde weergegeven en verdwijnt.

## Repareren

Aangezien het plaatsen van de bestelling niet wordt geblokkeerd, is het niet nodig om tussenliggende stappen uit te voeren.
