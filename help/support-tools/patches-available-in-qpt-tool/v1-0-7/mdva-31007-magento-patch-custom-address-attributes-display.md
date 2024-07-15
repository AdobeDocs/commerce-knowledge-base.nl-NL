---
title: 'MDVA-31007: display met aangepaste adreskenmerken'
description: De patch MDVA-31007 lost het probleem op waar de attributen van het douaneadres niet correct worden getoond in de de detailpagina van de orde in het Mijn gebied van de Rekening en in het achterste eind (in **Verkoop &gt; Orders** plaats). Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007: de vertoning van de attributen van het douaneadres

Het flard MDVA-31007 lost de kwestie op waar de attributen van het douaneadres niet correct in de pagina van de ordedetails in het Mijn gebied van de Rekening en in het achterste eind (in de **Verkoop > de plaats van Orden**) worden getoond. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de beheerder-back-end.
1. Navigeer aan **Opslag** > **Attributen** > **Adressen van de Klant**.
1. Twee kenmerken maken:

   * Plaats inputtype: *drop-down*.
   * Plaats inputtype: *Tekst*.

1. Navigeer aan **Opslag** > **Configuraties** > **Klant** > **de Configuraties van de Klant**.
1. Selecteer *van het 0} Gebied {als **Standaard opslag**mening.*
1. Breid de **sectie van het Malplaatje van 0} Adres uit.** De Tekst van de update ** *, Tekst Één Lijn*, en *HTML* om de twee douanekenmerken hierboven te omvatten:

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. Open Storefront.
1. Maken en aanmelden met een gebruiker.
1. Ga naar **Mijn Rekening** > **het boek van het Adres**, en voeg een nieuw adres toe (vul de twee douanekenmerken in).
1. Voeg een product aan de kar toe, en plaats een orde.
1. Voor de pagina van het ordesucces, klik op het **aantal van de Orde** verbinding.
1. Voor de pagina van de ordedetails, zie de **sectie van de Informatie van de Orde**.
1. Ga naar **Achtergrond** > **Verkoop** > **Orden**, klik op de bovengenoemde orde, en bekijk de **informatie van het Adres** sectie.

<u> Verwachte resultaten </u>:

Op zowel de voorzijde als de achterzijde worden het factuuradres en het verzendadres weergegeven zoals u had verwacht.

<u> Ware resultaten </u>:

Op zowel voor- als achterkant wordt het factuuradres niet correct weergegeven. De geselecteerde optie van het drop-down attribuut ontbreekt, en de waarde van het inputattribuut bevat de attributencode.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
