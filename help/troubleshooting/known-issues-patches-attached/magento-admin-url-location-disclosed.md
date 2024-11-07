---
title: Adobe Commerce Admin URL-locatie wordt weergegeven
description: Dit artikel bevat een patch voor het beveiligingsprobleem van Adobe Commerce, waarbij de URL-locatie van het deelvenster Beheer kan worden weergegeven. Als u de URL-locatie kent, kunt u aanvallen gemakkelijker automatiseren.
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Adobe Commerce Admin URL-locatie wordt weergegeven

Dit artikel bevat een patch voor het beveiligingsprobleem van Adobe Commerce, waarbij de URL-locatie van het deelvenster Beheer kan worden weergegeven. Als u de URL-locatie kent, kunt u aanvallen gemakkelijker automatiseren.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.X.X
* Adobe Commerce op locatie 2.X.X
* Magento Open Source 2.X.X

## Probleem

Er is een probleem ontdekt in Magento Open Source en Adobe Commerce dat kan worden gebruikt om de URL-locatie van het deelvenster Beheer weer te geven. Hoewel er momenteel geen reden is om aan te nemen dat deze kwestie rechtstreeks tot een compromis zou leiden, kan het door de URL-locatie te kennen eenvoudiger worden om aanvallen te automatiseren.

## Oplossing

Als u het probleem wilt verhelpen, past u de patch toe die aan dit artikel is gekoppeld. Klik op de volgende koppeling om deze te downloaden:

* Download [ PRODSECBUG-2432 \_EE \_2.1.17\_composer.patch ](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip) - voor versies 2.1.13-2.1.17, Adobe Commerce, Magento Open Source
* Download [ PRODSECBUG-2432 \_EE \_2.2.8\_composer.patch ](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip) - voor versies 2.2.0-2.2.8, alle uitgaven
* Download [ PRODSECBUG-2432 \_EE \_2.3.1 \_composer.patch ](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip) - voor versies 2.3.0-2.3.1, alle uitgaven

Als u geen patch ziet voor uw product/versie, dient u een upgrade uit te voeren naar de meest recente beveiligingsrelease en vervolgens de patch toe te passen.

Adobe beveelt ten zeerste aan de pleister zo snel mogelijk aan te brengen, zelfs als u geen symptomen van een aanval hebt ondervonden.

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe Commerce ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.

## Overige beveiligingsaanbevelingen

De Adobe adviseert ook sterk dat de handelaren hulpmiddelen opstellen om hun admin paneel, met inbegrip van tweefaste authentificatie, VPN, IP Voegend op lijst van gewenste personen, en meer te beveiligen. Raadpleeg de volgende blogs en documentatie voor meer informatie:

* [ 5 Onmiddellijke Acties aan Protect tegen de Aanvallen van de Kracht ](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [ Protect Uw Wachtwoord van de Installatie van het Magento Bezig Nieuwe Update ](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [ Beste praktijken van de Veiligheid ](https://magento.com/security/best-practices/security-best-practices)
* Toevoegend en Vormend Two-Factor Authentificatie in Adobe Commerce voor [ 2.4.x ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication)
