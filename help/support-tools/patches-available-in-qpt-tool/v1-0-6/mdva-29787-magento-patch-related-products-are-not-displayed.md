---
title: "MDVA-29787: verwante producten worden niet weergegeven"
description: De MDVA-29787-patch lost het probleem op waarbij **Gerelateerde Producten** niet worden weergegeven op de voorzijde van een Adobe Commerce-winkel. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd. De patch-id is MDVA-29787.
exl-id: ee060d7b-3b0e-4bd5-84e6-fbd6d2fa532f
feature: Cache, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# MDVA-29787: verwante producten worden niet weergegeven

Het flard MDVA-29787 lost de kwestie op waar **Verwante Producten** niet op een de winkelfront van Adobe Commerce worden getoond. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 geïnstalleerd is. De patch-id is MDVA-29787.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce op cloudinfrastructuur 2.3.3.

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.0.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De doelregel voor **Verwante Producten** werkt niet wanneer &quot;*één van*&quot;voorwaarde is wordt gebruikt voor **Producten aan Vertoning** in Commerce Admin.

>[!NOTE]
>
>Opmerking: deze patch herstelt geen bestaande doelregels. U moet bestaande doelregels opnieuw creëren.

<u> Stappen om </u> te reproduceren:

1. Creeer **Nieuw attribuut** (Voorbeeld: Test\_Attr).
   * Plaats **Type van Invoer van de Catalogus voor de Eigenaar van de Opslag** = *Tekst.*
   * In **Eigenschappen Storefront**, plaats **Gebruik voor de Voorwaarden van de Regel van de Bevordering** = *ja*.
1. Creeer **Nieuwe geplaatste Attributen** (Voorbeeld: Test\_Set).
1. Voeg het **Nieuwe Attribuut** aan de **Nieuwe Reeks van Attributen** toe (Voorbeeld: voeg &quot;Test\_Attr&quot;attribuut aan de &quot;Test\_Set&quot;kenmerkreeks toe).
1. Maak drie producten. Deze zijn bijvoorbeeld als volgt ingesteld:
   * Product1, test\_Attr = MAGT2NA\_Test3
   * Product2, Testen\_Attr = 24-MB02
   * Product3, Test\_Attr = 701644329389M
1. Creeer doel **Regel** (**Marketing**   > **Verwante Regels van het Product** en klik **voeg Regel** knoop toe.) met instellingen:
   * **is op** toe = *Verwante Producten*
   * **Producten om** aan te passen
   * Plaats het Nieuwe Attribuut u **in** **Stap 1 hierboven** creeerde om het attribuut van Product1 te zijn (Voorbeeld: Test\_Attr = MAGT2NA\_Test3).
   * **Producten aan Vertoning** = de attributen van de andere twee producten (Voorbeeld: attributen 24-MB02 en 701644329389M).
1. Sparen de **Regel**.
1. Voer indien nodig een nieuwe index uit.
1. Cache wissen.
1. Open Product1 op de voorzijde.

<u> Verwachte resultaten </u>:

De bijbehorende producten zijn aanwezig.

<u> Ware resultaten </u>:

De verwante producten ontbreken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
