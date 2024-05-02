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

De MDVA-13203 Adobe Commerce-patch verhelpt het probleem waarbij op uw site een onderhoudspagina wordt weergegeven en er *KRITIEK: SQLSTATE\[23000\]: schending van integriteitsbeperking* fouten in de `system.log`. De patch-id is MDVA-13203. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.2.4.

**Compatibel met Adobe Commerce-versies:** Adobe Commerce (alle implementatiemethoden) 2.3.0-2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren:</u>

1. Ga naar de desbetreffende URL.
1. U ziet de onderhoudspagina.
1. Controleer of de locatie geen onderhoudsstatus heeft via SSH:
   <pre> bin/magento-onderhoud:status Status: onderhoudsmodus is niet actief Lijst met vrijgestelde IP-adressen: geen</pre>
1. Kijk naar `system.log`:

<pre>grep Crip - i var/log/system.log |staart [2018-09-04 17]:05:18] report.CRITICAL: SQLSTATE[23000]: schending van integriteitsbeperking: 1062 Dubbele vermelding '4613' voor sleutel 'PRIMARY', query was: INSERT INTO ` search_tmp_5b8ebb4e994da5_88027 289` ("entity_id","score") VALUES (?, ?),... (?, ?), (?, ?) [] [2018-09-04 17]:05:21] report.CRITICAL: SQLSTATE[23000]: schending van integriteitsbeperking: 1062 Dubbele vermelding '4613' voor sleutel 'PRIMARY', query was: INSERT INTO ` search_tmp_5b8ebb51579943_52 333638` ("entity_id","score") VALUES (?, ?),...,(?, ?) [] [2018-09-04 17]:05:47] report.CRITICAL: SQLSTATE[23000]: schending van integriteitsbeperking: 1062 Dubbele vermelding '1350' voor sleutel 'PRIMARY', query was: INSERT INTO ` search_tmp_5b8ebb6b7028f4_6806 5024` ("entity_id`,"score`) VALUES (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, (?, ?) [] [2018-09-04 17]:05:47] report.CRITICAL: SQLSTATE[23000]: schending van integriteitsbeperking: 1062 Dubbele vermelding '1350' voor sleutel 'PRIMARY', query was: INSERT INTO ` search_tmp_5b8ebb6b785a9_2336 0993` ('entity_id`,'score`) VALUES (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, (?, ?) [] [] datum Tue Sept 4 17:06:11 UTC 2018</pre>

<u>Verwachte resultaten:</u> U moet de site zien.

<u>Werkelijke resultaten:</u> De onderhoudspagina wordt weergegeven vanwege problemen met de consistentie van de database.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
