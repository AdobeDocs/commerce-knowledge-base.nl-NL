---
title: 'MDVA-34867: De waarden van de voorwaardenveldset voor Geplande Update niet bewaard'
description: De patch MDVA-34867 lost het probleem op waar de waarde voor de voorwaarde in de nieuwe planningupdate niet wordt bewaard wanneer het uitgeven van een regel van de catalogusprijs. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: bf514ccc-bebd-4ed2-868f-28b02b1e253e
feature: Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-34867: De waarden van de voorwaardenveldset voor Geplande Update niet bewaard

De patch MDVA-34867 lost het probleem op waar de waarde voor de voorwaarde in de nieuwe planningupdate niet wordt bewaard wanneer het uitgeven van een regel van de catalogusprijs. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.4.0-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De waarde voor de voorwaarde in de nieuwe planningsupdate wordt niet opgeslagen bij het bewerken van een regel voor catalogusprijzen.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij Beheer.
1. Een **Catalogusregel** with **Voorwaarde** = &quot;*Categorie 1*&quot;.
1. Plan een update met een begindatum in de toekomst (Voorbeeld: morgen) en reeks **Voorwaarde** = &quot;*Categorie 2, 3*&quot; en sla de update op.
1. Klikken op **Weergeven/bewerken** voor de hierboven gemaakte update en controleer de voorwaardenvelden.

<u>Verwachte resultaten</u>:

De **Regels voor catalogi**  **Voorwaarde** = &quot;*Categorie 2, 3*&quot;, zoals verwacht.

<u>Werkelijke resultaten</u>:

De **Regels voor catalogi**  **Voorwaarde** = &quot;*Categorie 1*&quot;, wat betekent dat de update niet is opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
