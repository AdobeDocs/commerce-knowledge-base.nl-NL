---
title: 'MDVA-39605: Redis cache TTL (vervaldatum) heeft onjuiste waarde'
description: De patch MDVA-39605 lost het probleem op waar de Redis cache TTL (vervaldatum) een verkeerde waarde heeft. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-39605. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 7283838b-702d-4ddc-aa03-829dbf5aa91f
feature: Cache, Console, Services
role: Admin
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# MDVA-39605: Redis cache TTL (vervaldatum) heeft onjuiste waarde

De patch MDVA-39605 lost het probleem op waar de Redis cache TTL (vervaldatum) een verkeerde waarde heeft. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-39605. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De Redis cache-TTL (vervaldatum) heeft een onjuiste waarde.

<u>Stappen om te reproduceren</u>:

Om de moeilijke situatie te testen, spoel geheim voorgeheugen en open een configureerbaar product op de winkel. Open vervolgens een terminal (console) en volg de onderstaande stappen:

1. Voer de opdracht uit: `redis-cli`.
1. Uitvoeren `KEYS "*PRICE"` (er moet bijvoorbeeld slechts één sleutel in het resultaat aanwezig zijn, `zc:ti:e54_PRICE`). Kopieer de toets.
1. Uitvoeren `SMEMBERS` gevolgd door de toets van de vorige stap (bijvoorbeeld `SMEMBERS zc:ti:e54_PRICE`). Kopieer een willekeurige sleutel uit het resultaat (bijvoorbeeld e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Uitvoeren `KEYS "*<key>"` met de sleutelnaam van de vorige stap om de volledige zeer belangrijke naam (bijvoorbeeld `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`). Het resultaat mag slechts één toets bevatten (bijvoorbeeld `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Zoals u zult merken, is de volledige sleutelnaam eenvoudig de sleutelnaam met prefix &quot;`zc:k:`&quot;. Kopieer nu de volledige sleutelnaam.
1. Uitvoeren `HGETALL` gevolgd door de volledige sleutelnaam van Stap 4 om de waarde te controleren. De waarde zou geserialiseerde gegevens van bijbehorende producten van een verwant configureerbaar product moeten bevatten.
1. Uitvoeren `TTL` gevolgd door de volledige sleutelnaam van Stap 4 om te controleren of de sleutel een vervaldatum heeft. Het resultaat moet anders zijn dan **-1** en **-2** en moet ongeveer 2592000 (30 dagen) bedragen. Hoewel de vervaldatum in de code één jaar is, geldt voor de Redis-bibliotheek die in Adobe Commerce wordt gebruikt een maximale vervaldatum van 2592000.

<u>Verwachte resultaten</u>:

Vervallimiet is 2592000s

<u>Werkelijke resultaten</u>:

Vervallimiet is ingesteld op **-1** of **-2**.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
