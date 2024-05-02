---
title: "MDVA-28511: accentuerende letters hangen Payflow-betalingen aan"
description: De patch MDVA-28511 lost het probleem op wanneer betalingen via **Payflow Pro** niet zijn voltooid voor klantnamen met accenten letters.
exl-id: ecc827e3-2a1c-4f32-a0e2-9c5792483e7d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-28511: geaccentueerde brieven hangen Payflow-betalingen aan

De MDVA-28511-patch lost het probleem op wanneer betalingen via **Payflow Pro** niet volledig voor klantnamen met geaccentueerde letters.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.3.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.3.5-p1

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Vereiste</u>:

Inschakelen **Payflow Pro** betalingsmethode met creditcard.

<u>Stappen om te reproduceren</u>:

1. Voeg een product toe aan de winkelwagentje en ga verder met de afrekenpagina.
1. Stel de naam van een klant in met accenten. (Voorbeeld: **Ãtienne Ãillin**)
1. Ga door met de betalingsstappen.
1. Selecteren **Payflow Pro** als **Creditcard** en vult de creditcardgegevens in.
1. Klik op de knop **Opdracht plaatsen** knop.

<u>Verwachte resultaten</u>:

De bestelling wordt zonder problemen voltooid, zoals u had verwacht.

<u>Werkelijke resultaten</u>:

De volgorde is niet voltooid en in logboeken wordt een vergelijkbare fout weergegeven als in dit voorbeeld:

```php
[2020-06-12 07:50:23] report.CRITICAL: String to be escaped was not valid UTF-8 or could not be converted: �?tienne �?illini [] []
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
