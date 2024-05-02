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

Met de MDVA-30594-patch wordt het probleem opgelost waarbij de klant de pagina voor het succes van de bestelling niet ziet nadat een bestelling met meerdere adressen is geplaatst. Als u de bestellingen op de Commerce Admin controleert, worden twee bestellingen met dezelfde producten weergegeven in plaats van met de juiste producten. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce over wolkeninfrastructuur 2.3.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De veelvoudige adresorden voltooien niet met de pagina van het ordersucces en tonen twee orden met de zelfde producten in plaats van correcte degenen.

<u>Vereisten</u>:

Maak twee websites met winkels en winkelweergaven.

<u>Stappen om te reproduceren</u>:

1. Set **Bereik catalogusprijs** voor websitecatalogus (**Winkels** > **Instellingen** > **Configuratie** > **Catalogus** > **Catalogus** > **Prijs** > **Toepassingsgebied**).
1. Configureren **Vaste productbelastingen (FPT)** (**Winkels** > **Configuratie** > **Verkoop** > **Belasting** > **Vaste productbelastingen**):

   * **FPT inschakelen** = *Ja*
   * **Prijzen weergeven in de productlijst** = *Exclusief FPT*
   * **Prijzen weergeven op de pagina Productweergave** = *Exclusief FPT*
   * **Prijzen weergeven in verkoopmodules** = *Exclusief FPT* (Inclusief **FPT** beschrijving en eindprijs).
   * **Prijzen weergeven in e-mails** = *Exclusief FPT* (Inclusief **FPT** beschrijving en eindprijs).
   * **Belasting toepassen op FPT** = *Ja*
   * **FPT opnemen in subtotaal** = *Nee*

1. Een **FPT-kenmerk** en wijst u deze toe aan de standaardkenmerkset. (Zie [FPT configureren: een FPT-kenmerk maken](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute) in onze gebruikershandleiding).

1. Maak vier eenvoudige producten en stel de **FPT** **kenmerkwaarde** (Voorbeeld: stel het **FPT**   **kenmerkwaarde** = *Australië*).

1. Maak twee gebundelde producten met de volgende configuratie:

   * Definiëren **FPT**.
   * Set **Dynamische prijs** = *Nee*.
   * Set **Prijs** = *100*.
   * Bundelopties worden samen verzonden, allemaal gemarkeerd als standaard met **Prijssoort** = *Vast*.
   * Voeg twee van de eenvoudige die producten toe in Stap vier worden gecreeerd.

1. Maak een gebruikersaccount op de voorgrond. Werk het adres bij met het Australische adres (geef het land aan Australië op of welk land in de **FPT** instellen).

1. Voeg de twee gebundelde producten aan de kar toe.

1. Ga naar de pagina met winkelwagentjes en controleer of de **FPT** wordt correct weergegeven.

1. Klikken **Afhandeling met meerdere adressen**.

1. Voeg een tweede adres toe.

1. Wijs elk product aan een verschillend adres toe.

1. Doorgaan met het afrekenproces tot **Opdracht plaatsen**.

1. Klik op de knop **Opdracht plaatsen** knop.

<u>Verwachte resultaten</u>:

De volgorde met meerdere adressen wordt correct geplaatst.

<u>Werkelijke resultaten</u>:

Een bericht als: &quot;*Er is een fout opgetreden.*&quot; wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
