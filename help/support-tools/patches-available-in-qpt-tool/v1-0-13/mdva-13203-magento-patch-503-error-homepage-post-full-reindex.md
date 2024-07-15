---
title: 'MDVA-13203 patch: 503 error homepage post full redex'
description: '"De MDVA-13203 Adobe Commerce-patch verhelpt het probleem waarbij een onderhoudspagina wordt weergegeven op uw site. Er zijn *CRITICAL: SQLSTATE\[23000\]: schending van integriteitsbeperking*-fouten in het bestand System.log.". De patch-id is MDVA-13203. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 is geïnstalleerd.'''
exl-id: 8e09010b-9aa4-4a79-b546-a24bb72e0e40
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-13203 patch: 503 error homepage post full redex

De patch MDVA-13203 Adobe Commerce lost het probleem op waarbij uw site een onderhoudspagina weergeeft en er zijn *KRITISCHE: SQLSTATE\[23000\]: schending van integriteitsbeperking* fouten in `system.log`. De patch-id is MDVA-13203. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 geïnstalleerd is.

## Betrokken producten en versies

**het flard wordt gecreeerd voor versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.2.4.

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce (alle plaatsingsmethodes) 2.3.0-2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om te reproduceren:</u>

1. Ga naar de desbetreffende URL.
1. U ziet de onderhoudspagina.
1. Controleer of de locatie geen onderhoudsstatus heeft via SSH:
   <pre> bin/magento-onderhoud:status
    Status: de onderhoudsmodus is niet actief
    Lijst van vrijgestelde IP-adressen: geen</pre>
1. Kijk naar `system.log`:

<pre>grep Crip - i var/log/system.log |staart

[2018-09-04 17 :05: 18] report.CRITICAL: SQLSTATE[23000]: Schending van integriteitsbeperking: 1062 Dubbele ingang "4613"voor sleutel "PRIMARY", de vraag was: INSERT INTO ` search_tmp_5b8ebbbb b4e994da5_88027289" ("entity_id", "score") WAARDEN (?, ?),... (?, ?), (?, ?) [] []
[2018-09-04 17 :05: 21] report.CRITICAL: SQLSTATE[23000]: schending van integriteitsbeperking: 1062 Dubbele ingang "4613"voor sleutel "PRIMARY", de vraag was: TUSSENVOEGSEL IN ` search_tmp_5b8ebbb b51579943_52333638` ("entity_id","score") VALUES (?, ?),...,(?, ?) [] []
[2018-09-04 17 :05: 47] report.CRITICAL: SQLSTATE[23000]: schending van integriteitsbeperking: 1062 Dubbele ingang "1350"voor sleutel "PRIMARY", de vraag was: TUSSENVOEGSEL IN ` search_tmp_5b8ebbb b6b7028f4_68065024` ('entity_id`,'score`) VALUES (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, (? , ?), (?, ?), (?, ?), (?, ?), (?, ?) [] []
[2018-09-04 17 :05: 47] report.CRITICAL: SQLSTATE[23000]: schending van integriteitsbeperking: 1062 Dubbele ingang "1350"voor sleutel "PRIMARY", de vraag was: TUSSENVOEGSEL IN ` search_tmp_5b8ebbb b6b7885a9_23360993` ('entity_id`,'score`) VALUES (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, , ?), (?, ?), (?, ?), (?, ?), (?, ?) [] []

date

Tue Sep 4 17 :06: 11 UTC 2018</pre>

<u> Verwachte resultaten:</u> u zou de plaats moeten zien.

<u> Ware resultaten:</u> de onderhoudspagina toont wegens de kwesties van de gegevensbestandconsistentie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
