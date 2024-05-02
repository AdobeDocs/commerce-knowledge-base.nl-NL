---
title: 'MDVA-29042: globale categorietoestemmingen ongewijzigd'
description: De MDVA-29042-patch verhelpt het probleem waarbij catalogusmachtigingen automatisch werden gewijzigd in "*Allow*" nadat een nieuw product aan de gedeelde catalogus in Commerce Admin was toegevoegd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.3.6 met de B2B-extensie.
exl-id: 491b8881-87ec-4820-8f87-54961682e961
feature: Catalog Management, Categories, Customer Service, Roles/Permissions
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29042: algemene categorietoestemmingen ongewijzigd

De MDVA-29042-patch verhelpt het probleem waarbij catalogusmachtigingen zijn gewijzigd in &quot;*Toestaan*&quot; automatisch nadat een nieuw product is toegevoegd aan de gedeelde catalogus in Commerce Admin. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.3.6 met de B2B-extensie.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.3.3 tot 2.3.4-p2 met B2B-extensie

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u de selectie van een klantengroep in de algemene categorietoestemmingen in Commerce Admin opheft, wordt die klantgroep niet automatisch ingesteld op &quot;*Weigeren*&quot; in categorietoestemmingen.

<u>Vereisten</u>:

* B2B-exemplaar met een klantgroep gedefinieerd en geselecteerd onder **VOORRADEN** > **Configuratie** > **CATALOGUS** > **Catalogus** > **Categoriemachtigingen** voor:
   * **Browsercategorie toestaan**
   * **Productprijzen weergeven**
   * **Toevoegen aan winkelwagentje toestaan**
* Onder elke **Categorie**, wordt de klantengroep gedefinieerd als &quot;*Toestaan*&quot; voor:
   * **Browsercategorie**
   * **Productprijzen weergeven**
   * **Toevoegen aan winkelwagentje**

<u>Stappen om te reproduceren</u>:

1. Ga in Commerce Admin naar **VOORRADEN** > **Configuratie** > **CATALOGUS** > **Catalogus** > **Categoriemachtigingen** en deselecteer de klantengroep uit:
   * **Browsercategorie toestaan**
   * **Productprijzen weergeven**
   * **Toevoegen aan winkelwagentje toestaan**
1. Klik op de knop **Config opslaan** knop.
1. Wacht tot de indexen worden uitgevoerd.
1. Kijk naar **CATALOGUS** > **Categorieën** > **Categoriemachtigingen**.

<u>Verwachte resultaten</u>:

**Categoriemachtigingen** wordt ingesteld op &quot;*Weigeren*&quot; voor alle categorieën voor de klantengroep.

<u>Werkelijke resultaten</u>:

Geen wijziging in categorietoestemmingen voor de klantengroep.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.

Raadpleeg de volgende artikelen in onze documentatie voor ontwikkelaars voor meer informatie over de functionaliteit van B2B-bedrijven:

* [B2B-ontwikkelaarsgids](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Bedrijfsrollen beheren](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Referentie voor configuratiepaden voor Adobe Commerce Enterprise B2B-extensies](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
