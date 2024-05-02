---
title: "MDVA-27664 patch: date of geboorting account error"
description: De MDVA-27664-patch lost het probleem op waarbij de geboortedatum van een klantenaccount hoger kan zijn dan vandaag.
exl-id: c669764e-b4a5-4031-92ac-1156755e9a0a
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-27664 patch: date of geboorterekening error

De MDVA-27664-patch lost het probleem op waarbij de geboortedatum van een klantenaccount hoger kan zijn dan vandaag.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.3.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de beheerder.
1. Set **Landinstelling** = *en\_GB* (VK) voor een gebruiker.
1. Een klant bewerken.
1. Selecteer een geboortedatum na de twaalfde van een maand van dit jaar.

<u>Verwachte resultaten</u>:

De geboortedatum is geldig, zodat de klantgegevens kunnen worden opgeslagen, zoals u had verwacht.

<u>Werkelijke resultaten</u>:

De klantgegevens kunnen niet worden opgeslagen omdat er een validatiefout optreedt:

```php
The Date of Birth should not be greater than today.
```

waarbij in plaats van de datum-notatie DD/MM/JJJJ, de datum wordt behandeld als de datum-notatie MM/DD/JJJJ.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
