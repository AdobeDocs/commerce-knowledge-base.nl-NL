---
title: Beheerder kan geen bestelling/herschikking maken wanneer betaling via Braintree is ingeschakeld
description: Dit artikel bevat een patch voor de Adobe Commerce 2.4.5-uitgave, waarbij een Admin-gebruiker geen bestellingen kan maken en geen bestellingen kan bijstellen voor klanten als de betalingsmethode voor Braintreeën is ingeschakeld.
exl-id: 8840aecb-21d9-4965-8c09-395e2d263aaa
feature: Admin Workspace, Native Luma Frontend Development, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Beheerder kan geen bestelling/herschikking maken wanneer betaling via Braintree is ingeschakeld

Dit artikel bevat een patch voor de Adobe Commerce 2.4.5-uitgave, waarbij een Admin-gebruiker geen bestellingen kan maken en geen bestellingen kan bijstellen voor klanten als de betalingsmethode voor Braintreeën is ingeschakeld.

## Betrokken producten en versies

* Adobe Commerce over wolkeninfrastructuur 2.4.5
* Adobe Commerce op locatie 2.4.5
* Magento Open Source 2.4.5

## Probleem

<u> Stappen om </u> te reproduceren:

1. De integratie van de kern Braintree wordt gebruikt (**slaat** > **Configuraties** > **Verkoop** > **de Methode van de Betaling** > **Braintree**) op.
1. Plaats een bestelling met Luma Storefront.
1. Ga naar Admin UI > **Verkoop**.
1. Of probeer om een nieuwe orde voor een klant tot stand te brengen, of naar een eerder geplaatste orde te gaan en op **te klikken herordent**.

<u> Verwacht resultaat </u>:

Gebruikers met beheerdersrechten kunnen met succes bestellingen en opnieuw bestellingen voor klanten maken wanneer de betalingsmethode voor Braintreeën is ingeschakeld.

<u> Werkelijk resultaat </u>:

Gebruikers met beheerdersrechten kunnen geen orders maken of orders opnieuw ordenen voor klanten als de betalingsmethode voor Braintreeën is ingeschakeld en de volgende fout wordt geretourneerd:

```bash
report.CRITICAL: Error: Call to a member function getMethodInstance() on null in /app/vendor/paypal/module-braintree-core/Block/Form.php:174
```

## Oorzaak

Onjuiste klasseafhankelijkheden (`vendor/paypal/module-braintree-core/Block/Form.php`)

## Oplossing

Pas de patch toe die in dit artikel is opgenomen.

## Reparatie

De patch is aan dit artikel gekoppeld. Klik op de volgende koppeling om deze te downloaden:

[BUNDLE-3137-composer.patch.zip](assets/BUNDLE-3137-composer.patch.zip)

>[!NOTE]
>
>Daarnaast voor Adobe Commerce op producten met cloudinfrastructuur: Adobe heeft de oplossing opgenomen in de cloudpatches voor Commerce versie 1.0.18. Gelieve te verwijzen naar [ de versienota&#39;s van de Huur van de Wolk voor de versie van Commerce ](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html) in onze ontwikkelaarsdocumentatie om instructies te vinden bij het toepassen van het recentste pakket.

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce over wolkeninfrastructuur 2.4.5
* Adobe Commerce op locatie 2.4.5
* Magento Open Source 2.4.5

>[!NOTE]
>
>De patch is niet compatibel met andere Adobe Commerce- en Magento Open Source-versies en -versies.

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze basis van steunkennis voor instructies wordt verstrekt.
