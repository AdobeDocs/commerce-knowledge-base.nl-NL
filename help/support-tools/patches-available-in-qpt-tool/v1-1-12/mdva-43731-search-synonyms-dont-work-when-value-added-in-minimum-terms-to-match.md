---
title: '"MDVA-43731: De Synoniemen van het onderzoek werken niet wanneer de waarde in "Minimumtermijnen aan Gelijke"wordt toegevoegd'
description: De patch MDVA-43731 verhelpt het probleem waarbij Zoeksynoniemen niet meer werken wanneer een waarde wordt toegevoegd in "Minimumvoorwaarden voor overeenkomst". Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43731. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: b795989c-d10b-443e-aebe-f3859930396a
feature: Cache, Marketing Tools, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-43731: De Synoniemen van het onderzoek werken niet wanneer de waarde in &quot;Minimumtermijnen aan Gelijke&quot;wordt toegevoegd

De patch MDVA-43731 verhelpt het probleem waarbij Zoeksynoniemen niet meer werken wanneer een waarde wordt toegevoegd in &quot;Minimumvoorwaarden voor overeenkomst&quot;. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43731. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Zoeksynoniemen werken niet meer wanneer een waarde wordt toegevoegd in &quot;Minimumvoorwaarden voor overeenkomst&quot;.

<u>Stappen om te reproduceren</u>:

1. Installeer Adobe Commerce met voorbeeldgegevens.
1. Configureer Elasticsearch7 als zoekprogramma.
1. Zoek naar het woord &quot;Jasje&quot;. Er wordt een lijst met producten weergegeven.
1. De parameter toevoegen [4&lt;60%] in **Configuratie** > **Catalogus** > **Catalogus zoeken** > **Minimale voorwaarden**.
1. Wis het Geheime voorgeheugen Config en doe een herdex.
1. Zoek opnieuw naar het woord &quot;Jasje&quot;. U ziet dat er een lijst met producten wordt weergegeven.
1. Ga naar **Marketing** > **SEO &amp; Search** > **Synoniemen zoeken**.
1. Creeer de Synoniemen van het Onderzoek door de volgende synoniemen toe te voegen: jasje, bagtecs, express plus.
1. Voer een herindex uit.
1. Zoek een product met een van de synoniemen. Bijvoorbeeld jasje.

<u>Verwachte resultaten</u>:

Je krijgt dezelfde productlijst als voorheen in de zoekresultaten.

<u>Werkelijke resultaten</u>:

Er wordt geen product weergegeven in de zoekresultaten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
