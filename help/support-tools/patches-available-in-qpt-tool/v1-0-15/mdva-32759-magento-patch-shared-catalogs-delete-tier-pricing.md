---
title: 'MDVA-32759 patch: shared catalogs delete tier pricing'
description: Met de MDVA-32759-patch wordt het probleem opgelost waarbij gedeelde catalogi de bestaande laagprijzen verwijderen.
exl-id: c6192d2f-cd25-483e-ba69-01ca62996faf
feature: B2B, Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# MDVA-32759-patch: gedeelde catalogi verwijderen prijsopgave

Met de MDVA-32759-patch wordt het probleem opgelost waarbij gedeelde catalogi de bestaande laagprijzen verwijderen.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Eerste vereisten </u>:

Installeer Adobe Commerce met B2B, met **toegelaten Eigenschappen B2B**.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag > Configuratie > Eigenschappen B2B > laat Bedrijf** en **Gedeelde Catalogus** toe.
1. Voer `bin/magento cron:run` uit.
1. Creeer een eenvoudig product, klik op **Geavanceerde Prijsbepaling**, en voeg **Catalogus en de prijs van de Rij** toe, en bewaar het dan.
1. Ga naar **Catalogus > Gedeelde Catalogus > Prijsbepaling en Structuur** plaatsen, klik op **vormen**, en van dat drop-down menu, schrap alle opties en sparen.
1. Voer `bin/magento cron:run` uit.
1. Open het hierboven gemaakte product en controleer de geavanceerde prijzen.

<u> Verwachte resultaten </u>:

De prijzen op het niveau mogen niet uit de producten worden verwijderd nadat alle producten uit de gedeelde openbare catalogus zijn verwijderd, zoals verwacht.

<u> Ware resultaten </u>:

De laagprijzen worden verwijderd nadat alle producten uit de gedeelde openbare catalogus zijn verwijderd.


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
