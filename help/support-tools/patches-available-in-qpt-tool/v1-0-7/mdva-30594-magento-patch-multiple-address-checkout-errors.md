---
title: 'MDVA-30594: meerdere afrekenfouten van adressen'
description: Met de MDVA-30594-patch wordt het probleem opgelost waarbij de klant de pagina voor het succes van de bestelling niet ziet nadat een bestelling met meerdere adressen is geplaatst. Als u de bestellingen op de Commerce Admin controleert, worden twee bestellingen met dezelfde producten weergegeven in plaats van met de juiste producten. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.4.2.
exl-id: 7560cc39-ff0d-4313-979e-5cd588554c1d
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# MDVA-30594: Meerdere uitcheckfouten

Met de MDVA-30594-patch wordt het probleem opgelost waarbij de klant de pagina voor het succes van de bestelling niet ziet nadat een bestelling met meerdere adressen is geplaatst. Als u de bestellingen op de Commerce Admin controleert, worden twee bestellingen met dezelfde producten weergegeven in plaats van met de juiste producten. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce over wolkeninfrastructuur 2.3.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De veelvoudige adresorden voltooien niet met de pagina van het ordersucces en tonen twee orden met de zelfde producten in plaats van correcte degenen.

<u> Eerste vereisten </u>:

Maak twee websites met winkels en winkelweergaven.

<u> Stappen om </u> te reproduceren:

1. Plaats **Reikwijdte van de Prijs van de Catalogus** voor websitecatalogus (**Slaat** > **Montages** > **Configuratie** > **Catalogus** > **Catalogus** > **Prijs** > **Reikwijdte**).
1. Vorm **Vaste Belastingen van het Product (FPT)** (**Opslag** > **Configuratie** > **Verkoop** > **Belasting** > **Vaste Belastingen van het Product**):

   * **laat FPT** toe = *ja*
   * **de Prijzen van de Vertoning in de Lijst van het Product** = *exclusief FPT*
   * **de Prijzen van de Vertoning op de Pagina van de Mening van het Product** = *exclusief FPT*
   * **de Prijzen van de Vertoning in de Modules van de Verkoop** = *exclusief FPT* (met inbegrip van **FPT** beschrijving en definitieve prijs).
   * **de Prijzen van de Vertoning in E-mail** = *exclusief FPT* (met inbegrip van **FPT** beschrijving en definitieve prijs).
   * **pas Belasting op FPT** toe = *ja*
   * **omvat FPT in Subtotal** = *Nr*

1. Creeer een **attributen van FPT**, en wijs het aan de standaardkenmerkreeks toe. (Zie [ Vormend FPT: Creeer een attribuut FPT ](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute) in onze gebruikersgids).

1. Creeer vier eenvoudige producten, en plaats **FPT** **attributenwaarde** (Voorbeeld: plaats **FPT**   **attributenwaarde** = *Australië*).

1. Maak twee gebundelde producten met de volgende configuratie:

   * Bepaal **FPT**.
   * Plaats **Dynamische Prijs** = *Nr*.
   * Plaats **Prijs** = *100*.
   * De opties van de bundel samen verscheepten, allen duidelijk als gebrek met **Type van Prijs** = *Vast*.
   * Voeg twee van de eenvoudige die producten toe in Stap vier worden gecreeerd.

1. Maak een gebruikersaccount op de voorgrond. Werk het adres met Australisch adres bij (plaats land aan Australië of welk land in **FPT** opstelling werd gebruikt).

1. Voeg de twee gebundelde producten aan de kar toe.

1. Ga naar de wortelpagina, en controleer dat **FPT** correct toont.

1. Klik **Controle met Veelvoudige Adressen**.

1. Voeg een tweede adres toe.

1. Wijs elk product aan een verschillend adres toe.

1. Ga met het controleproces tot **de Orde van de Plaats** verder.

1. Klik de **knoop van de Orde van de Plaats**.

<u> Verwachte resultaten </u>:

De volgorde met meerdere adressen wordt correct geplaatst.

<u> Ware resultaten </u>:

Een bericht als, &quot;*een fout is voorgekomen.* wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
