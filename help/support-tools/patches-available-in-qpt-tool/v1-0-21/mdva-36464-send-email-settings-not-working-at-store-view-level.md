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

De patch MDVA-36464 verhelpt het probleem waarbij de instellingen voor het verzenden van e-mail niet werken op het niveau van de winkelweergave. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 geïnstalleerd is. De patch-id is MDVA-36464. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.4.0-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Vereiste:</u>

Installeer schone Adobe Commerce.

<u> Stappen om </u> te reproduceren:

1. Creeer een extra website, opslag, en opslagmening (in dit Voorbeeld, is de tweede website *website2*).
1. Maak **E-mail- bericht** op het globale niveau in **opslag** > **Config** > **Geavanceerd** > **Systeem** > **Verzendende Montages van de Post** onbruikbaar.
1. Laat **E-mail- bericht** op het *website2* niveau toe (**onbruikbaar maken E-mail Mededelingen** = *Nr*).
1. In Admin, creeer een nieuwe gebruiker, en wijs het aan *website2* toe.
1. In Admin, op de klant geeft pagina uit, klik **Wachtwoord van het Terugstellen** voor de klant hierboven in Stap 4 wordt gecreeerd.

<u> Verwachte resultaten </u>:

Zowel worden het **welkome e-mail** en **terugstellen wachtwoord e-mail** verzonden, zoals verwacht, omdat **E-mailmededelingen** = *Nr* voor de tweede website (Voorbeeld: *website2*) onbruikbaar maken.

<u> Ware resultaten </u>:

* Het **welkome e-mail** na de verwezenlijking van de nieuwe klant wordt niet teweeggebracht.
* Het **teruggestelde wachtwoord e-mail** wordt niet teweeggebracht.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
