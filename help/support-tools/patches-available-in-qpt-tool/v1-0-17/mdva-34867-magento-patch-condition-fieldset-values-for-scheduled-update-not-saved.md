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

De patch MDVA-34867 lost het probleem op waar de waarde voor de voorwaarde in de nieuwe planningupdate niet wordt bewaard wanneer het uitgeven van een regel van de catalogusprijs. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.4.0-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De waarde voor de voorwaarde in de nieuwe planningsupdate wordt niet opgeslagen bij het bewerken van een regel voor catalogusprijzen.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij Beheer.
1. Creeer de Regel van de a **Catalogus** met **Voorwaarde** = &quot;*Categorie is 1*&quot;.
1. Plan een update met een begindatum in de toekomst (Voorbeeld: morgen) en plaats **Voorwaarde** = &quot;*Categorie is 2, 3*&quot;, en sparen de update.
1. Klik op **Mening/geef** voor de hierboven gecreeerde update uit, en controleer de voorwaardengebieden.

<u> Verwachte resultaten </u>:

De **** Voorwaarde van de Regel van de Catalogus **** = &quot;*Categorie is 2, 3*&quot;, zoals verwacht.

<u> Ware resultaten </u>:

De **** Voorwaarde van de Regel van de Catalogus **** = &quot;*Categorie is 1*&quot;, betekenend dat de update niet werd bewaard.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
