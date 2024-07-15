---
title: 'MDVA-33606: Gebruikers krijgen een fout wanneer ze CMS-pagina opslaan die is toegewezen aan de hiërarchie'
description: De patch MDVA-33606 lost het probleem op waar de gebruikers *Unieke schending van de beperking gevonden* fout wanneer het bewaren van een CMS pagina die aan hiërarchieboom wordt toegewezen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 is geïnstalleerd. De patch-id is MDVA-33606. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: cdefece5-6d13-4003-87e9-810c665e940c
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-33606: Gebruikers krijgen een fout wanneer ze CMS-pagina opslaan die is toegewezen aan de hiërarchie

Het flard MDVA-33606 lost de kwestie op waar de gebruikers *Unieke gevonden beperkingsschending* fout krijgen wanneer het opslaan van een CMS pagina die aan hiërarchieboom wordt toegewezen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 geïnstalleerd is. De patch-id is MDVA-33606. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het proberen om een CMS pagina te bewaren die aan hiërarchieboom wordt toegewezen, krijgen de gebruikers het volgende foutenbericht: *Unieke gevonden beperkingsschending*.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe CMS-pagina. Stel het bereik in op Alle winkelweergaven. Dit is uw CMS-pagina 1.
1. Maak een nieuwe winkelweergave. Dit is je winkelweergave 2.
1. Ga naar **Inhoud** > **Hiërarchie** > voeg CMS Pagina 1 aan hiërarchieboom toe.
1. Wijzig het bereik in Winkelweergave 2.
   * Schakel &quot;De hiërarchie van bovenliggende knooppunten gebruiken&quot; uit.
   * Voeg CMS-pagina 1 toe aan dit bereik en sla deze op.
1. Wijzig nu het bereik in Standaardwinkelweergave.
   * Schakel &quot;De hiërarchie van bovenliggende knooppunten gebruiken&quot; uit.
   * Voeg CMS-pagina 1 toe aan dit bereik en sla deze op.
1. Ga naar **Inhoud** > **Pagina&#39;s** > **voeg Nieuwe Pagina** toe.
   * Titreer de pagina als pagina 2.
   * In de Pagina in de sectie van Websites, wijs aan Alle Mening van de Opslag en beide opslagmeningen (de Mening van de StandaardOpslag en Mening 2 van de Opslag) toe en klik **sparen Pagina**.
1. Open het tabblad Hiërarchie op de pagina CMS-bewerking.
   * Wijs Pagina 2 toe aan de knoop van de Mening 2 van de Opslag, Standaardknoop, en Al knoop Websites.

<u> Verwachte resultaten </u>:

U kunt de CMS-pagina zonder fouten toewijzen aan alle drie knooppunten.

<u> Ware resultaten </u>:

U krijgt de volgende fout: *Unieke gevonden beperkingsschending*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
