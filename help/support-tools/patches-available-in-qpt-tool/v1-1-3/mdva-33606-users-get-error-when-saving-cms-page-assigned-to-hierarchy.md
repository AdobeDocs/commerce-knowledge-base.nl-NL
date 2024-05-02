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

De MDVA-33606-patch lost het probleem op waar de gebruikers terecht komen *Unieke schending van beperking gevonden* fout bij het opslaan van een CMS-pagina die is toegewezen aan de hiërarchiestructuur. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 is geïnstalleerd. De patch-id is MDVA-33606. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer gebruikers een CMS-pagina proberen op te slaan die is toegewezen aan een hiërarchische structuur, krijgen ze het volgende foutbericht: *Unieke schending van beperking gevonden*.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe CMS-pagina. Stel het bereik in op Alle winkelweergaven. Dit is uw CMS-pagina 1.
1. Maak een nieuwe winkelweergave. Dit is je winkelweergave 2.
1. Ga naar **Inhoud** > **Hiërarchie** > Voeg CMS-pagina 1 toe aan de hiërarchiestructuur.
1. Wijzig het bereik in Winkelweergave 2.
   * Schakel &quot;De hiërarchie van bovenliggende knooppunten gebruiken&quot; uit.
   * Voeg CMS-pagina 1 toe aan dit bereik en sla deze op.
1. Wijzig nu het bereik in Standaardwinkelweergave.
   * Schakel &quot;De hiërarchie van bovenliggende knooppunten gebruiken&quot; uit.
   * Voeg CMS-pagina 1 toe aan dit bereik en sla deze op.
1. Ga naar **Inhoud** > **Pagina&#39;s** > **Nieuwe pagina toevoegen**.
   * Titreer de pagina als pagina 2.
   * Wijs in de sectie Pagina in websites aan Alle winkelweergaven en beide winkelweergaven toe (Standaardwinkelweergave en Winkelweergave 2) en klik op **Pagina opslaan**.
1. Open het tabblad Hiërarchie op de pagina CMS-bewerking.
   * Wijs Pagina 2 toe aan de knoop van de Mening 2 van de Opslag, Standaardknoop, en Al knoop Websites.

<u>Verwachte resultaten</u>:

U kunt de CMS-pagina zonder fouten toewijzen aan alle drie knooppunten.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op: *Unieke schending van beperking gevonden*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
