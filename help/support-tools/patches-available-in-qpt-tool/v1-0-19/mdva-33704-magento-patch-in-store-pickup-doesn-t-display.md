---
title: "MDVA-33704 patch: In-store pickup does not display"
description: Met de MDVA-33704-patch wordt het probleem opgelost waarbij producten met de optie Ophalen in de winkel niet als een verzendmethode worden weergegeven.
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-33704-patch: Ophalen in winkel wordt niet weergegeven

Met de MDVA-33704-patch wordt het probleem opgelost waarbij producten met de optie Ophalen in de winkel niet als een verzendmethode worden weergegeven.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 geïnstalleerd is. De patch-id is MDVA-33704. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.4.0-p1

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op-gebouw en Adobe Commerce op wolkeninfrastructuur 2.4.0-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Vereiste </u>:<br>

**Keuze in Bewaren** toegelaten

<u> Stappen om </u> te reproduceren:

1. Voeg een product toe aan de kar.
1. Ga naar Afhandeling.
1. Voeg verzendgegevens toe en kies een andere verzendmethode dan het ophalen in de winkel.
1. Selecteer **ga aan betaling** verder, maar ga dan niet aan de betalingspagina te werk.
1. In plaats daarvan ga terug naar de **Contact &amp; die** sectie verschepen.
1. Selecteer **Bestelwagen**.
1. Selecteer **Opslag** en **klik aan Betaling**.
1. Je verzendadres wordt automatisch ingevoerd als factuuradres.
1. Vernieuw de webpagina.

<u> Verwachte resultaten </u>:

De optie Ophalen in de winkel wordt als een verzendmethode weergegeven, zoals u had verwacht.

<u> Ware resultaten </u>:

De optie Ophalen in winkel wordt niet weergegeven als verzendmethode.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
