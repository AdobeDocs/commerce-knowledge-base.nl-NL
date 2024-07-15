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

Het flard MDVA-29042 bevestigt de kwestie waar de catalogustoestemmingen werden veranderd in &quot;*toestaan*&quot;automatisch nadat een nieuw product aan de gedeelde catalogus in Commerce Admin werd toegevoegd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce 2.3.6 met de B2B-extensie.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.3.3 tot 2.3.4-p2 met B2B-extensie

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het schrappen van een klantengroep van de globale categorietoestemmingen in Commerce Admin plaatst automatisch niet die klantengroep aan &quot;*ontkent*&quot;binnen categorietoestemmingen.

<u> Eerste vereisten </u>:

* B2B instantie met een klantengroep die onder **wordt bepaald en wordt geselecteerd STOORT** > **Configuratie** > **CATALOGUS** > **Catalogus** > **Toestemmingen van de Categorie** voor:
   * **toestaan het doorbladeren Categorie**
   * **Prijzen van het Product van de Vertoning**
   * **Toestaan Toevoegend aan Kar**
* Onder elke **Categorie**, wordt de klantengroep bepaald zoals &quot;**&quot;toestaat voor:
   * **het doorbladeren Categorie**
   * **Prijzen van het Product van de Vertoning**
   * **toevoegen aan Kar**

<u> Stappen om </u> te reproduceren:

1. In Commerce Admin, ga **>** Configuratie **>** CATALOG **>** Catalogus **>** de Toestemmingen van de Categorie **en de - selecteer de klantengroep van:**
   * **toestaan het doorbladeren Categorie**
   * **Prijzen van het Product van de Vertoning**
   * **Toestaan Toevoegend aan Kar**
1. Klik **sparen Config** knoop.
1. Wacht tot de indexen worden uitgevoerd.
1. Bekijk **CATALOG** > **Categorieën** > **Toestemmingen van de Categorie**.

<u> Verwachte resultaten </u>:

**de Toestemmingen van de Categorie** zullen aan &quot;*worden geplaatst ontkennen*&quot;voor alle categorieën voor de klantengroep.

<u> Ware resultaten </u>:

Geen wijziging in categorietoestemmingen voor de klantengroep.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.

Raadpleeg de volgende artikelen in onze documentatie voor ontwikkelaars voor meer informatie over de functionaliteit van B2B-bedrijven:

* [ B2B de Gids van de Ontwikkelaar ](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [ beheer bedrijfrollen ](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [ de configuratiewegen van de Uitbreiding van de Onderneming B2B van Adobe Commerce verwijzing ](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
