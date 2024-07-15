---
title: "MDVA-28651: B2B - offertes traag te laden"
description: De patch MDVA-28651 lost het probleem op waarbij verschillende prestatieproblemen optreden bij het laden van aanhalingstekens. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9 is geïnstalleerd. Het probleem zou volgens de planning worden opgelost in Adobe Commerce versie 2.4.2.
exl-id: 2d0bfbba-cdf3-4f9e-a900-ce42909fac8e
feature: B2B, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-28651: B2B - Aanhalingstekens traag te laden

De patch MDVA-28651 lost het probleem op waarbij verschillende prestatieproblemen optreden bij het laden van aanhalingstekens. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9 geïnstalleerd is. Het probleem zou volgens de planning worden opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloud-infrastructuur 2.3.4.
* De patch is ook compatibel met de volgende Adobe Commerce-versies: Adobe Commerce op locatie en Adobe Commerce op cloud-infrastructuur 2.3.0-2.3.5-p1, 2.4.0 en 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Prestatieproblemen op de pagina met de prijsopgave voor klanten:

* dubbel laden van de prijsopgave: eerst met hele pagina, tweede door Ajax verzoek.
* een lus waarbij elk aanhalingsteken van de plug-in wordt geladen.
* het tweemaal laden van de citaatpunten toen het citaat in de momentopname werd omgezet.

<u> Stappen om te reproduceren </u>

1. 40+ aanhalingstekens hebben toegewezen aan een klant.
1. Login en doorblader de **Mijn Citaten** pagina.

<u> Werkelijk resultaat </u>

De reactietijd om de inhoud van **volledig te laden Mijn Citaten** pagina (lading van pagina + gegevens die in het net worden getoond) is ~ 45 seconden.

<u> Verwacht resultaat </u>

De reactietijd om de inhoud van de **Mijn Citaten** pagina volledig te laden zou minder dan 45 seconden moeten zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
