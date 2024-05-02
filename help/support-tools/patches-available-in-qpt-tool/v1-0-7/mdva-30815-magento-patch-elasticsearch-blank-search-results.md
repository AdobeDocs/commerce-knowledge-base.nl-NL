---
title: "MDVA-30815: Elasticsearch blanco zoekresultaten"
description: De patch MDVA-30815 verhelpt het probleem waarbij Elasticsearch een lege pagina weergeeft wanneer de limiteringsopties van de zoekresultaten worden gewijzigd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.3.5.
exl-id: dbe41a43-e248-407e-8cf9-319ad5843935
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30815: Elasticsearch blanco zoekresultaten

De patch MDVA-30815 verhelpt het probleem waarbij Elasticsearch een lege pagina weergeeft wanneer de limiteringsopties van de zoekresultaten worden gewijzigd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.3.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce over wolkeninfrastructuur 2.3.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u Elasticsearch gebruikt en de limiteringsopties van de zoekresultaten wijzigt, geeft Adobe Commerce een lege pagina weer.

<u>Vereisten</u>:

Elasticsearch is **enabled**. Ga naar **VOORRADEN** > **Instellingen** > **Configuratie** > **Catalogus** > **Catalogus zoeken**.

<u>Stappen om te reproduceren</u>:

1. Ga naar uw site.
1. Zoeken naar een product in het hoofdzoekveld.
1. Nadat de pagina&#39;s met zoekresultaten zijn weergegeven, klikt u op de laatste pagina op de pagina met zoekresultaten.
1. Selecteren **xx per pagina tonen** in de limiteringsoptie. Zorg ervoor dat dit een verschillende grens van het aantal van het onderzoeksresultaat is dan momenteel gevormd.

<u>Verwachte resultaten</u>:

Op de pagina wordt het geconfigureerde aantal productresultaten weergegeven.

<u>Werkelijke resultaten</u>:

Lege pagina wordt weergegeven. Deze fout is ook zichtbaar in het dialoogvenster `var/report` : *\`&quot;0&quot;:&quot;SQLSTATE\[42000\]: Syntaxisfout of toegangsfout: 1064 U hebt een fout in uw SQL-syntaxis; raadpleeg de handleiding die overeenkomt met uw MySQL-serverversie voor de juiste syntaxis voor gebruik dichtbij&#39;\`*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
