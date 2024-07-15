---
title: 'MDVA-30265: link bijhouden in e-mail retourneert 404 Pagina niet gevonden'
description: Met de MDVA-30265-patch wordt het probleem van de fout "404 Pagina niet gevonden" opgelost wanneer de klant op de koppeling voor het volgen van de verzending klikt in het bevestigingsbericht voor de bestelling. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 53e1ca98-dfa0-445b-a71a-56fd01b630ec
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# MDVA-30265: link bijhouden in e-mail retourneert 404 Pagina niet gevonden

Met de MDVA-30265-patch wordt het probleem van de fout &quot;404 Pagina niet gevonden&quot; opgelost wanneer de klant op de koppeling voor het volgen van de verzending klikt in het bevestigingsbericht voor de bestelling. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 t/m 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Nadat de verzending is gemaakt voor een geplaatste bestelling, wordt een e-mail verzonden naar de klant met trackinggegevens en een koppeling om de bestelling te volgen. Wanneer de klant echter op de koppeling voor het bijhouden van de verzending in de e-mail klikt, wordt de fout &quot;404 pagina niet gevonden&quot; geretourneerd.

<u> Stappen om </u> te reproduceren:

1. Adobe Commerce 2.4 installeren. Voor stappen, verwijs naar [ installeer Adobe Commerce gebruikend Composer ](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) in onze ontwikkelaarsdocumentatie.
1. Plaats een bestelling.
1. Ga naar het Admin paneel > **Verkoop** > **Orden**. Zoek de volgorde die u zojuist hebt gemaakt en open deze.
1. Maak een verzending en voeg een trackingnummer toe (vervoerder = aangepaste waarde). Voor stappen, verwijs naar [ Order Management > Creërend een Verzending ](https://docs.magento.com/user-guide/sales/shipments-create.html) in onze gebruikersgids.
1. Je ontvangt een e-mail. Klik op de koppeling voor bijhouden om te controleren of deze werkt.
1. Maak een factuur. Voor stappen, verwijs naar [ Order Management > Creërend een factuur ](https://docs.magento.com/user-guide/sales/invoice-create.html) in onze gebruikersgids. Klik vervolgens nogmaals op de bovenstaande koppeling voor bijhouden.

<u> Verwachte resultaten </u>:

De koppeling voor bijhouden werkt ook nadat de factuur is gemaakt.

<u> Ware resultaten </u>:

Nadat de factuur is gemaakt, werkt de koppeling voor bijhouden niet meer en wordt een foutpagina &quot;404 pagina niet gevonden&quot; geretourneerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
