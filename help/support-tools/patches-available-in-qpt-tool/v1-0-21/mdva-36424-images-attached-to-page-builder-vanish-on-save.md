---
title: 'MDVA-36424: Afbeeldingen die aan de paginaontwikkelaar zijn gekoppeld, verdwijnen bij opslaan.'
description: De patch MDVA-36424 lost het probleem op waarbij de afbeeldingen die aan elementen van de paginaontwikkelaar zijn gekoppeld, verdwijnen wanneer de categorie voor de tweede keer wordt opgeslagen in het geval van meerdere websites, waarbij de basis-URL van de standaardwebsite anders is dan de admin-URL. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 is geïnstalleerd. De patch-id is MDVA-36424. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: ae15db2d-0d9f-48c1-87e4-61da1558a57c
feature: Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-36424: Afbeeldingen die aan de paginaontwikkelaar zijn gekoppeld, verdwijnen bij opslaan

De patch MDVA-36424 lost het probleem op waarbij de afbeeldingen die aan elementen van de paginaontwikkelaar zijn gekoppeld, verdwijnen wanneer de categorie voor de tweede keer wordt opgeslagen in het geval van meerdere websites, waarbij de basis-URL van de standaardwebsite anders is dan de admin-URL. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 geïnstalleerd is. De patch-id is MDVA-36424. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.3.6

**Compatibel met de versies van het Magento:**

Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Mediaafbeeldingen die zijn gekoppeld aan elementen van de paginabuilder, worden niet opgeslagen als de basis-URL van de achterste URL afwijkt van de basisURL van de winkel.

<u> Stappen om </u> te reproduceren:

1. Maak een tweede website - website2.
1. Stel een andere basis-URL in voor website2 (de basis-URL die in de beheerder wordt gebruikt, moet anders zijn dan de tweede website).
1. Plaats de tweede website als standaardwebsite (**Slaat** > *Montages* > **Alle Sporen** > selecteren de tweede website > plaatste als *Gebrek*).
1. Navigeer naar de categoriepagina op de achtergrond en ga naar de categoriebewerkingsweergave.
1. Navigeer aan **Inhoud** > *Beschrijving*.
1. Voeg een kolom toe aan de inhoud en stel een achtergrondafbeelding in met de mediagalerie.
1. Sla de categorie op.
1. Ga naar de **Inhoud** > *Beschrijving* opnieuw; u zult het bewaarde beeld correct zien.
1. Sla de rubriek opnieuw op.
1. Ga naar de **Inhoud** > *Beschrijving*.

<u> Verwachte resultaten </u>:

De afbeelding wordt niet verwijderd wanneer u de categorie opslaat.

<u> Ware resultaten </u>:

De afbeelding wordt verwijderd nadat de categorie een tweede keer is opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
