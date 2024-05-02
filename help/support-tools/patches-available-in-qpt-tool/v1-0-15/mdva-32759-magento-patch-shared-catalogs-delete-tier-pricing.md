---
title: 'MDVA-32759 patch: shared catalogs delete tier pricing'
description: Met de MDVA-32759-patch wordt het probleem opgelost waarbij gedeelde catalogi de bestaande laagprijzen verwijderen.
exl-id: c6192d2f-cd25-483e-ba69-01ca62996faf
feature: B2B, Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# MDVA-32759-patch: gedeelde catalogi verwijderen prijsopgave

Met de MDVA-32759-patch wordt het probleem opgelost waarbij gedeelde catalogi de bestaande laagprijzen verwijderen.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Vereisten</u>:

Installeer Adobe Commerce met B2B, met **B2B-functies** ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Storingen > Configuratie > B2B-functies > Bedrijf inschakelen** en **Gedeelde catalogus**.
1. Uitvoeren `bin/magento cron:run`.
1. Een eenvoudig product maken, klik op **Geavanceerde prijzen** en toevoegen **Catalogus en prijs op de schaal** en sla deze vervolgens op.
1. Ga naar **Catalogus > Gedeelde catalogus > Prijzen en structuur instellen**, klikt u op **Configureren** en in dat keuzemenu deselecteert u alle opties en slaat u deze op.
1. Uitvoeren `bin/magento cron:run`.
1. Open het hierboven gemaakte product en controleer de geavanceerde prijzen.

<u>Verwachte resultaten</u>:

De prijzen op het niveau mogen niet uit de producten worden verwijderd nadat alle producten uit de gedeelde openbare catalogus zijn verwijderd, zoals verwacht.

<u>Werkelijke resultaten</u>:

De laagprijzen worden verwijderd nadat alle producten uit de gedeelde openbare catalogus zijn verwijderd.


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
