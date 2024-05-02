---
title: 'MDVA-39713: De gebruiker kan de begintijd van de actieve geplande update bewerken'
description: De patch MDVA-39713 verhelpt het probleem waarbij een gebruiker de begintijd van een actieve geplande update kan bewerken. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-39713. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: c7221fdb-5fc0-4179-8d4c-c9e1f0d00692
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-39713: de gebruiker kan de begintijd van de actieve geplande update bewerken

De patch MDVA-39713 verhelpt het probleem waarbij een gebruiker de begintijd van een actieve geplande update kan bewerken. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-39713. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker kan de begintijd voor een actieve geplande update bewerken.

<u>Stappen om te reproduceren</u>:

1. Nieuwe CMS-pagina&#39;s maken.
1. Selecteren **Nieuwe update plannen** en stelt de **Begindatum** naar huidige +1 minuut.
1. Activeer Geplande Update door het bevel in werking te stellen `bin/magento cron:run --group=staging` in de lokale omgeving. Wacht een paar minuten en controleer of het schema actief is.
1. Zodra het programma actief is, vernieuw de pagina.
1. Klikken **Weergeven/bewerken** in de Geplande sectie van Veranderingen.
1. Bewerk de tijd door +2 minuten toe te voegen en sla de wijziging op.
1. Sla de CMS-pagina op.
1. Voer opnieuw de volgende opdracht uit: `bin/magento cron:run --group=staging`.
1. Klikken **Weergeven/bewerken** van de geplande update.

<u>Verwachte resultaten</u>:

De gebruiker kan de begintijd voor een actieve geplande update niet bewerken.

<u>Werkelijke resultaten</u>:

De gebruiker krijgt een fout als *Item (Magento\Cms\Model\Page) met dezelfde id bestaat al.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
