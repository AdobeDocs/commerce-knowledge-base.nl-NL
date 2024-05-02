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

Met de MDVA-29446-patch wordt het probleem opgelost waarbij een verzendmethode die niet van toepassing is, wordt weergegeven bij de opties voor de verzendmethode voor uitchecken en, indien geselecteerd, een foutbericht &quot;*Drager met een dergelijke methode is niet null, forfaitair*.&quot; worden weergegeven. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd. Het probleem wordt opgelost in latere Adobe Commerce-versies.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce over wolkeninfrastructuur 2.3.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3-2.4.0.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Problemen

Je hebt een verzendmethode die niet van toepassing is, maar die wel wordt weergegeven bij de opties voor de verzendmethode voor afhandeling. Je kunt deze niet-relevante verzendmethode selecteren.

<u>Stappen om te reproduceren</u>:

1. Installeer schone 2.3-ontwikkelaars.
1. Vlakke snelheid inschakelen en instellen:

   * Schip naar landen van toepassing = *Specifieke landen*
   * Schip naar specifieke landen = *Antarctica*
   * Methode weergeven indien niet van toepassing = *Ja*

1. Alle andere verzendmethoden uitschakelen.
1. Ga naar de frontend, creeer een klant met een adres van de V.S.
1. Selecteer een item en klik op **Toevoegen aan winkelwagentje**.
1. Klik op het winkelwagentje en klik **Doorgaan naar Afhandeling**.

<u>Werkelijke resultaten</u>:

1. Op de **Verzending** pagina, ziet u het volgende:

   * Vlakke snelheid is zichtbaar
   * Plat tarief is $0
1. Nadat de gebruiker klikt **Volgende**, krijgt de gebruiker de volgende fout:

*&quot;Drager met dergelijke methode niet gevonden: null, flatrate&quot;*

<u>Verwachte resultaten</u>:

* De prijs van de verzendmethode is niet zichtbaar als de verzendmethode niet van toepassing is.
* De **Volgende** mag niet actief zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
