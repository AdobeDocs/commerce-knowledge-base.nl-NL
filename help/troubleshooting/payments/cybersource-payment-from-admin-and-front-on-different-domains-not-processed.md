---
title: Cyberbronbetaling van Admin en front op verschillende domeinen die niet zijn verwerkt
description: Dit artikel biedt een patch voor de bekende Adobe Commerce 2.3.0-beperking die verband houdt met het niet kunnen verwerken van Cybersource-betalingen van zowel de storefront als de Commerce Admin, als deze zich op verschillende domeinen bevinden.
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Cyberbronbetaling van Admin en front op verschillende domeinen die niet zijn verwerkt

Dit artikel biedt een patch voor de bekende Adobe Commerce 2.3.0-beperking die verband houdt met het niet kunnen verwerken van Cybersource-betalingen van zowel de storefront als de Commerce Admin, als deze zich op verschillende domeinen bevinden.

>[!NOTE]
>
>De belangrijkste integratie van Adobe Commerce Cybersource-betalingen is sinds 2.3.3 verouderd en zal in 2.4.0 volledig worden verwijderd. Gebruik in plaats hiervan de [&#x200B; officiële uitbreiding &#x200B;](https://marketplace.magento.com/cybersource-global-payment-management.html) van Marketplace.

## Probleem

Dankzij de vorige implementatie van de Cybersource-integratie konden betalingen van slechts één domein worden verwerkt. Dientengevolge, als uw Adobe Commerce storefront op verschillend domein van Commerce Admin is, krijgt u de volgende fout wanneer het proberen om een orde te plaatsen gebruikend Cybersource in Admin: &quot; *lading ontkend door x-Kader-Opties: https://%your\_domain%/cybersource/SilentOrder/TokenResponse/ staat geen dwars-oorsprong het framing toe.*..&quot;

<u> Stappen om </u> te reproduceren:

1. Stel Admin in op een ander subdomein.
1. Vorm Cybersource voor de opslag onder **Opslag** > Montages > **Configuratie** > **Verkoop** > **de Methoden van de Betaling** > **CyberSource**.
1. Ga naar **Verkoop** > **Orders**.
1. Nieuwe bestelling maken.
1. Nieuwe klant maken.
1. Voer klantgegevens in.
1. Voer de bestelgegevens in (producten, verzendmethode).
1. Selecteer Cybersource als betalingsmethode.
1. Bestelling verzenden.

<u> Verwacht resultaat </u>: De orde wordt geplaatst zonder kwesties.

<u> Ware resultaat </u>: De pagina van de Orde toont een ladingspictogram, maar de orde wordt nooit geplaatst. De fout wordt getoond in console.

## Oplossing

De bijgevoegde patch biedt de verbetering voor de integratie met Cybersource. Na het toepassen van het flard, moet u één meer profiel met Cybersource voor verwerkingsbetalingen in Admin tot stand brengen, en de vereiste geloofsbrieven in de configuratie Cybersource in Commerce Admin onder **toe te voegen** > Montages > **Configuratie** > **Verkoop** > **de Methoden van de Betaling** > **CyberSource**.

>[!NOTE]
>
>De verbetering is opgenomen in de Adobe Commerce-infrastructuur op locatie en in de cloudinfrastructuur 2.2.9 en 2.3.1.

## Reparatie

Er zijn verschillende patches aan dit artikel gekoppeld, verschillende patches voor verschillende versies. Als u een patch wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

* [MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch downloaden](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [MDVA-8609\_EE\_2.2\_COMPOSER\_v2.patch downloaden](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch downloaden](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch downloaden](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## Compatibele Adobe Commerce-versies

De patches zijn gemaakt voor een bepaalde versie die is vermeld in de naam van het patchbestand. MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch is bijvoorbeeld gemaakt voor Adobe Commerce 2.1.9 en is de beste patch die kan worden gebruikt voor deze versie.

De patches zijn ook compatibel met de volgende versies:

* Adobe Commerce op locatie 2.1.3-2.1.17; Adobe Commerce op cloudinfrastructuur 2.1.5-2.12 (MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce op locatie 2.2.0-2.2.3; Adobe Commerce op cloudinfrastructuur 2.2.0-2.2.3 (MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch)
* Adobe Commerce op locatie 2.2.4-2.2.7; Adobe Commerce op cloudinfrastructuur 2.2.4-2.2.7 (MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce op locatie 2.2.8, 2.3.0; Adobe Commerce op cloudinfrastructuur 2.3.0 (MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## Hoe een pleister aanbrengen

Voor instructies, zie [&#x200B; hoe te om een componentenflard toe te passen die door Adobe &#x200B;](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis wordt verstrekt.

## Bijgevoegde bestanden
