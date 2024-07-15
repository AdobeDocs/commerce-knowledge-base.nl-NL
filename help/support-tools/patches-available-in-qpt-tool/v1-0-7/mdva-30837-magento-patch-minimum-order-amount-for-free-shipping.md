---
title: "MDVA-30837: minimumbestelling voor gratis verzending"
description: De flard MDVA-30837 voegt configuratieopties voor de vrije verzendberekening toe zodat kan de gebruiker het Minimale Bedrag van de Orde vormen om Vrije Verzending te krijgen die op Subtotal (of het Grote Totaal) wordt gebaseerd. Zo kunnen lokale aanpassingen voor belasting- en verzendmethoden worden toegepast. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 64716d08-4ce0-40d5-aeb7-242e2aa85bb0
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# MDVA-30837: minimumbestelbedrag voor gratis verzending

De flard MDVA-30837 voegt configuratieopties voor de vrije verzendberekening toe zodat kan de gebruiker het Minimale Bedrag van de Orde vormen om Vrije Verzending te krijgen die op Subtotal (of het Grote Totaal) wordt gebaseerd. Zo kunnen lokale aanpassingen voor belasting- en verzendmethoden worden toegepast. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce over cloudinfrastructuur 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De flard mDVA-30837 voegt de configuratie toe die het **Minimale Bedrag van de Orde** plaatsen te vormen om vrije verzending te krijgen die op Subtotal (of het Grote Totaal) wordt gebaseerd:

* **omvat Belasting aan Bedrag**: *ja/Nr* in de Vrije Verzendmethode configuratie.
   * Wanneer **omvat Belasting aan Bedrag** aan *ja* wordt geplaatst, wordt het minimumordebedrag berekend als Subtotaal + Belasting - Korting.
   * Wanneer **omvat Belasting aan Bedrag** aan *Nr* wordt geplaatst, wordt het minimumordebedrag berekend als Subtotaal - Korting.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > Montages > **Configuratie** > **Verkoop** > **Belasting** en plaats het volgende:

   * De Berekening van de belasting die op *wordt gebaseerd Verzendadres*
   * Laat Grensoverschrijdende handel toe: *Nr*
   * Toon Productieprijzen in Catalogus: *exclusief Belasting*
   * Toon Verzendprijzen: *exclusief Belasting*
   * De Prijzen van de vertoning: *exclusief Belasting*
   * Subtotaal van de vertoning: *exclusief Belasting*
   * Verzendbedrag weergeven: *exclusief belasting*
   * De Wrappende Prijzen van het Gift van de vertoning: *exclusief Belasting*
   * De Prijzen van de Vertoning Gedrukte Kaart: *exclusief Belasting*
   * Omvat Belasting in het Totaal van de Orde: *ja*
   * Volledige Overzicht van de Belasting van de vertoning: *ja*

1. Ga naar **Verkoop** > **Verschepende Montages** > **Vrij Verschepend** en plaats **MinimumBedrag van de Orde** = *30*.
1. Ga naar **de Marketing** > Bevorderingen > **Regels van de Prijs van de Kar** en creeer een nieuwe prijsregel (voor gedetailleerde stappen, verwijs naar [ creeer een Regel van de Prijs van de Kar ](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html) in onze gebruikersgids).

   * Coupon Code = *Specifieke coupon*.
   * Voorwaarden: Subtotaal is gelijk aan of groter dan $25.
   * Handelingen: Vrij Verzenden = *voor zendingen met overeenkomende items* .

1. Maak een product met een prijs van $ 23,10.
1. Voeg de CA-belasting toe aan de standaardbelastingregel.
1. Voeg dit product toe aan het winkelwagentje.
1. Ontvang een verzendprijsopgave - na belastingen is het Eindtotaal = $25,01 en wordt gratis verzending toegepast.
1. Pas de waardeboncode toe - deze is niet geldig omdat het subtotaal (exclusief belasting) $23,10 is.

<u> Verwachte resultaten </u>:

Er is een extra configuratie die - omvat Belasting aan Bedrag plaatst: *ja*/ *Nr* in de Vrije Verzendingsmethodeconfiguratie:

* Wanneer omvat Belasting aan Bedrag wordt geplaatst aan *ja*, wordt het Minimale Bedrag van de Orde berekend als Subtotaal + Belasting - Korting.
* Wanneer omvat Belasting aan Bedrag wordt geplaatst aan *Nr*, wordt het Minimale Bedrag van de Orde berekend als Subtotaal - Korting.

<u> Ware resultaten </u>:

De voorwaarde voor de regel voor de prijs bij gratis verzending kan alleen worden gebaseerd op het subtotaal, terwijl de methode voor gratis verzending alleen kan worden gebaseerd op het Eindtotaal.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
