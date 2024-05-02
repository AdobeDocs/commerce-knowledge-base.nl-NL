---
title: 'MDVA-12304: 503 error on store front and cookie error'
description: Met deze MDVA-12304 Adobe Commerce-patch worden 503 fouten op winkelfronten opgelost. *Kan het cookie niet verzenden. Het maximumaantal cookies wordt overschreden.* foutbericht in logboeken. Dit is een bekend Adobe Commerce 2.2.5-probleem. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd.
exl-id: b4b1a2f7-f328-488f-86b8-576b908792fb
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# MDVA-12304: fout van 503 op de voorzijde van de opslag en koekjesfout

Met deze MDVA-12304 Adobe Commerce-patch worden 503 fouten op winkelfronten opgelost, met *Kan het cookie niet verzenden. Het maximumaantal cookies wordt overschreden.* foutbericht in logboeken. Dit is een bekend Adobe Commerce 2.2.5-probleem. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd.

## Betrokken producten en versies

* **De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op locatie 2.2.5.
* **Compatibel met Adobe Commerce-versies:** Adobe Commerce (alle implementatiemethoden) 2.x.x.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klanten krijgen een fout van 503 wanneer het navigeren van de opslagvoorzijde. In de `var/log/exception.log` bestand bevat het volgende foutbericht *Kan het cookie niet verzenden. Het maximumaantal cookies wordt overschreden.*

Het probleem doet zich voor omdat de Adobe Commerce-standaardlimiet voor cookies is ingesteld op 50. Als de browser van de client deze limiet bereikt, genereert Commerce een uitzondering. De oplossing in de pleister verhoogt de limiet van 200 cookies.

<u>Stappen om te reproduceren:</u>

De fout van 503 kan op om het even welk punt tonen wanneer de klant probeert om binnen te registreren en hun karretje te bekijken.

In de `var/log/exception.log` bestand bevat het volgende foutbericht *Kan het cookie niet verzenden. Het maximumaantal cookies wordt overschreden.*

<u>Werkelijk resultaat:</u> De klant kan zijn winkelwagentje niet controleren of zijn bestelling voltooien.

<u>Verwacht resultaat:</u> De klant kan zijn winkelwagentje controleren en de bestelling voltooien.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.


## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
