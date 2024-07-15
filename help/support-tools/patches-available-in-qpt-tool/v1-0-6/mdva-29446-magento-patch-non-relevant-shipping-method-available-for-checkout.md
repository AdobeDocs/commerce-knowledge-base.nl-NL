---
title: "MDVA-29446: Niet-relevante verzendmethode beschikbaar voor afhandeling"
description: Met de MDVA-29446-patch wordt het probleem opgelost waarbij een verzendmethode die niet van toepassing is, wordt weergegeven bij de opties voor de verzendmethode voor afhandeling en, indien deze optie is geselecteerd, een foutbericht "*Drager met deze methode niet null, flat rate*" wordt gevonden. worden weergegeven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd. Het probleem wordt opgelost in latere Adobe Commerce-versies.
exl-id: 74de5ec4-1f57-4d63-8fbc-614b23783ee3
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-29446: Niet-relevante verzendmethode beschikbaar voor afhandeling

Het flard MDVA-29446 lost de kwestie op waar een verschepende methode die niet van toepassing is op de controle verschepende methodopties, en indien geselecteerd, een foutenmelding &quot;*Drager met dergelijke methode niet ongeldig, vlak tarief* vond.&quot; worden weergegeven. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 geïnstalleerd is. Het probleem wordt opgelost in latere Adobe Commerce-versies.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce over wolkeninfrastructuur 2.3.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3-2.4.0.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Problemen

Je hebt een verzendmethode die niet van toepassing is, maar die wel wordt weergegeven bij de opties voor de verzendmethode voor afhandeling. Je kunt deze niet-relevante verzendmethode selecteren.

<u> Stappen om </u> te reproduceren:

1. Installeer schone 2.3-ontwikkelaars.
1. Vlakke snelheid inschakelen en instellen:

   * Schip aan Toepasselijke Landen = *Specifieke Landen*
   * Schip aan Specifieke Landen = *Antarctica*
   * Toon Methode als Niet van toepassing = *ja*

1. Alle andere verzendmethoden uitschakelen.
1. Ga naar de frontend, creeer een klant met een adres van de V.S.
1. Selecteer een punt en klik **toevoegen aan Kar**.
1. Klik op de kar en klik **ga aan Controle** te werk.

<u> Ware resultaten </u>:

1. Op de **Verschepende** pagina, ziet u het volgende:

   * Vlakke snelheid is zichtbaar
   * Plat tarief is $0
1. Nadat de gebruiker **daarna** klikt, krijgt de gebruiker de volgende fout:

*&quot;Drager met dergelijke methode niet gevonden: ongeldig, afvlakken&quot;*

<u> Verwachte resultaten </u>:

* De prijs van de verzendmethode is niet zichtbaar als de verzendmethode niet van toepassing is.
* De **Volgende** knoop zou niet actief moeten zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
