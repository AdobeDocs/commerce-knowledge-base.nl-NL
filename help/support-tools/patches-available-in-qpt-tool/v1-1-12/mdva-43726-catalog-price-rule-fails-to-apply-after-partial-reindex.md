---
title: "MDVA-43726: Catalogusprijsregel is niet van toepassing na gedeeltelijke herindexering"
description: De patch MDVA-43726 verhelpt het probleem waarbij de regel voor catalogusprijzen die is gebaseerd op kenmerkovereenkomsten op archiefniveau niet van toepassing is na gedeeltelijke herindex. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43726. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 70e7e1d2-e601-4fed-9274-a1a619de29e1
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-43726: Catalogusprijsregel is niet van toepassing na gedeeltelijke herindexering

De patch MDVA-43726 verhelpt het probleem waarbij de regel voor catalogusprijzen die is gebaseerd op kenmerkovereenkomsten op archiefniveau niet van toepassing is na gedeeltelijke herindex. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43726. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De regel voor catalogusprijzen die is gebaseerd op kenmerkovereenkomsten op archiefniveau wordt niet toegepast na gedeeltelijke herindex.

<u>Stappen om te reproduceren</u>:

1. Stel de indexeermodus in om volgens schema te werken.
1. Maak twee configureerbare productkenmerken. Bijvoorbeeld: Kleur (visuele staal) en Grootte (tekststaal).
1. Creeer een configureerbaar product gebruikend beide attributen die in Stap 2 worden gecreeerd.
1. Maak na het maken van de producten een **Ja/Nee** type en maak het in de regelvoorwaarden zichtbaar.
1. Voeg dit kenmerk toe aan de standaardkenmerkset.
1. Een regel voor catalogusprijzen maken die moet worden toegepast wanneer dit kenmerk is ingesteld op **Ja**.
1. Open een van de eenvoudige producten met betrekking tot het configureerbare product.
1. Het bereik voor het opslaan van de weergave en het bijwerken van de kenmerkwaarde wijzigen in **Ja**.
1. Voer de `CRON` en controleer de prijs aan de voorzijde.
1. Voer een volledige herindex uit. Controleer nogmaals de prijs aan de voorzijde.
1. Werk de configureerbare productcategorie bij.
1. Voer de `CRON` en controleer de prijs opnieuw aan de voorzijde.

<u>Verwachte resultaten</u>:

De catalogusregel wordt correct toegepast zonder een volledige herindex met behulp van incrementele indexen.

<u>Werkelijke resultaten</u>:

De catalogusregel wordt niet toegepast zonder een volledige herindex uit te voeren.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
