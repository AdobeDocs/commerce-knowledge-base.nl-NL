---
title: 'MDVA-36464: E-mailinstellingen verzenden die niet werken op winkelweergaveniveau'
description: De patch MDVA-36464 verhelpt het probleem waarbij de instellingen voor het verzenden van e-mail niet werken op het niveau van de winkelweergave. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 is geïnstalleerd. De patch-id is MDVA-36464. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: cdf7e208-90ee-4711-8407-026da42fe3c8
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-36464: Verzend e-mailinstellingen die niet werken op winkelweergaveniveau

De patch MDVA-36464 verhelpt het probleem waarbij de instellingen voor het verzenden van e-mail niet werken op het niveau van de winkelweergave. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 is geïnstalleerd. De patch-id is MDVA-36464. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.4.0-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Vereiste:</u>

Installeer schone Adobe Commerce.

<u>Stappen om te reproduceren</u>:

1. Een extra website maken, opslaan en opslaan (in dit voorbeeld is de tweede website *website2*).
1. Uitschakelen **E-mailmelding** op mondiaal niveau **Winkel** > **Config** > **Geavanceerd** > **Systeem** > **Instellingen voor verzending per post**.
1. Inschakelen **E-mailmelding** op de *website2* niveau (**E-mailcommunicatie uitschakelen** = *Nee*).
1. Maak in Admin een nieuwe gebruiker en wijs deze toe aan de *website2*.
1. Klik in Beheer op de pagina Bewerken door de klant op **Wachtwoord opnieuw instellen** voor de klant die hierboven in Stap 4 wordt gecreeerd.

<u>Verwachte resultaten</u>:

Beide **welkome e-mail** en de **wachtwoord opnieuw instellen** worden verzonden, zoals verwacht, omdat **E-mailcommunicatie uitschakelen** = *Nee* voor de tweede website (voorbeeld: *website2*).

<u>Werkelijke resultaten</u>:

* De **welkome e-mail** nadat de oprichting van de nieuwe klant niet is gestart.
* De **wachtwoord opnieuw instellen** wordt niet geactiveerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
