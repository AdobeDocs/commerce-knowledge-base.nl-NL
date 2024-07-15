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

De patch MDVA-30815 verhelpt het probleem waarbij Elasticsearch een lege pagina weergeeft wanneer de limiteringsopties van de zoekresultaten worden gewijzigd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.3.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce over wolkeninfrastructuur 2.3.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u Elasticsearch gebruikt en de limiteringsopties van de zoekresultaten wijzigt, geeft Adobe Commerce een lege pagina weer.

<u> Eerste vereisten </u>:

Elasticsearch wordt **toegelaten**. Ga naar **BEWAREN** > **Montages** > **Configuratie** > **Catalogus** > **het Onderzoek van de Catalogus**.

<u> Stappen om </u> te reproduceren:

1. Ga naar uw site.
1. Zoeken naar een product in het hoofdzoekveld.
1. Nadat de pagina&#39;s met zoekresultaten zijn weergegeven, klikt u op de laatste pagina op de pagina met zoekresultaten.
1. Selecteer **tonen xx per pagina** van de limiter optie. Zorg ervoor dat dit een verschillende grens van het aantal van het onderzoeksresultaat is dan momenteel gevormd.

<u> Verwachte resultaten </u>:

Op de pagina wordt het geconfigureerde aantal productresultaten weergegeven.

<u> Ware resultaten </u>:

Lege pagina wordt weergegeven. Deze fout kan ook worden gezien in `var/report` : *\` ` 0&#39;:&quot;SQLSTATE\[42000\]: de fout van de Syntaxis of toegangsschending: 1064 u hebt een fout in uw SQL syntaxis; controleer de handleiding die aan uw MySQL serverversie voor de juiste syntaxis aan gebruik dichtbij&#39;\ `* beantwoordt

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
