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

De flard MDVA-30837 voegt configuratieopties voor de vrije verzendberekening toe zodat kan de gebruiker het Minimale Bedrag van de Orde vormen om Vrije Verzending te krijgen die op Subtotal (of het Grote Totaal) wordt gebaseerd. Zo kunnen lokale aanpassingen voor belasting- en verzendmethoden worden toegepast. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce over cloudinfrastructuur 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De patch MDVA-30837 voegt de configuratie toe die om te vormen **Minimumbedrag bestelling** instellen om gratis verzending te krijgen op basis van het subtotaal (of Eindtotaal):

* **Inclusief BTW op bedrag**: *Ja/Nee* in de configuratie van de methode Free Shipping.
   * Wanneer **Inclusief BTW op bedrag** is ingesteld op *Ja*, wordt het minimale bestelbedrag berekend als Subtotaal + BTW - Korting.
   * Wanneer **Inclusief BTW op bedrag** is ingesteld op *Nee*, wordt het minimumorderbedrag berekend als Subtotaal - Korting.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > Instellingen > **Configuratie** > **Verkoop** > **Belasting** en stelt u het volgende in:

   * Belastingberekening op basis van *Verzendadres*
   * Grensoverschrijdende handel inschakelen: *Nee*
   * Productieprijzen weergeven in catalogus: *Exclusief belasting*
   * Verzendprijzen weergeven: *Exclusief belasting*
   * Prijzen weergeven: *Exclusief belasting*
   * Subtotaal weergeven: *Exclusief belasting*
   * Verzendbedrag weergeven: *Exclusief belasting*
   * Weergaveprijzen voor cadeauverpakking: *Exclusief belasting*
   * Afgedrukte kaartprijzen weergeven: *Exclusief belasting*
   * Inclusief BTW in totaal bestelling: *Ja*
   * Volledige belastingoverzicht weergeven: *Ja*

1. Ga naar **Verkoop** > **Verzendinstellingen** > **Gratis verzending** en instellen **Minimumbedrag bestelling** = *30*.
1. Ga naar **Marketing** > Promoties > **Lijnen met winkelprijzen** en maak een nieuwe prijsregel (voor gedetailleerde stappen raadpleegt u [Een regel voor een startprijs maken](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html) in onze gebruikershandleiding).

   * Coupon Code = *Specifieke coupon*.
   * Voorwaarden: Subtotaal is gelijk aan of groter dan $25.
   * Handelingen: Gratis verzending = *Voor overbrengingen met overeenkomende items*.

1. Maak een product met een prijs van $ 23,10.
1. Voeg de CA-belasting toe aan de standaardbelastingregel.
1. Voeg dit product toe aan het winkelwagentje.
1. Ontvang een verzendprijsopgave - na belastingen is het Eindtotaal = $25,01 en wordt gratis verzending toegepast.
1. Pas de waardeboncode toe - deze is niet geldig omdat het subtotaal (exclusief belasting) $23,10 is.

<u>Verwachte resultaten</u>:

Er is een extra configuratie-instelling - Inclusief BTW op bedrag: *Ja*/*Nee* in configuratie van de methode voor gratis verzending:

* Als Inclusief BTW op bedrag is ingesteld op *Ja*, wordt het minimumbedrag van de Orde berekend als Subtotaal + Belasting - Korting.
* Als Inclusief BTW op bedrag is ingesteld op *Nee*, wordt het minimumbedrag van de Orde berekend als Subtotaal - Korting.

<u>Werkelijke resultaten</u>:

De voorwaarde voor de regel voor de prijs bij gratis verzending kan alleen worden gebaseerd op het subtotaal, terwijl de methode voor gratis verzending alleen kan worden gebaseerd op het Eindtotaal.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
