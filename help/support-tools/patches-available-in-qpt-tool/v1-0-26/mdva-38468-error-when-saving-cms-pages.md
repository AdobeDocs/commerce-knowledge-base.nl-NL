---
title: 'MDVA-38468: Een foutbericht ontvangen bij het opslaan van CMS-pagina'
description: '''De MDVA-38468 Adobe Commerce-patch verhelpt het probleem waarbij gebruikers het foutbericht krijgen: *Item met dezelfde id bestaat al,* wanneer een CMS-pagina wordt opgeslagen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 is geïnstalleerd. De patch-id is MDVA-38468. Dit probleem is opgelost in Adobe Commerce 2.3.6. "'
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468: Ontvang een foutbericht wanneer u CMS-pagina opslaat

Het flard MDVA-38468 Adobe Commerce van lost de kwestie op waar de gebruikers het foutenbericht krijgen: *Punt met zelfde identiteitskaart &quot;PAGE_ID&quot;bestaat reeds,* wanneer het bewaren van een CMS pagina. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 geïnstalleerd is. De patch-id is MDVA-38468. De kwestie is opgelost in Adobe Commerce 2.3.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
Adobe Commerce op cloudinfrastructuur 2.3.2-p2

**Compatibel met de versies van Adobe Commerce:**
Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.2-2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het proberen om een CMS pagina te bewaren, ontvangt u het volgende foutenbericht: *Punt met zelfde identiteitskaart &quot;PAGE_ID&quot;bestaat reeds.*

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe website + Winkel + Voorvertoning.
1. Maak nog een website + Winkel + Winkelweergave.
1. Ga naar **Inhoud** > **Hiërarchie** > voeg om het even welke bestaande CMS pagina aan hiërarchieboom toe.
1. Ga naar **Inhoud** > **Pagina&#39;s** > **voeg Nieuwe Pagina** toe:
   * Voeg een titel toe.
   * In de sectie Pagina in websites wijst u beide gemaakte winkels toe.
   * Wijs in de sectie Hiërarchie aan elke gewenste categorie toe.
   * **sparen en ga uitgeven** voort.

<u> Verwachte resultaten </u>:

De pagina wordt zonder fout opgeslagen.

<u> Ware resultaten </u>:

De pagina wordt bewaard, maar u krijgt het volgende foutenbericht: *Punt (Magento\VersionsCms\Model\Hierarchy\Node) met zelfde identiteitskaart &quot;PAGE_ID&quot;bestaat reeds.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
