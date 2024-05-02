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

De MDVA-29787-patch lost het probleem op waarbij **Verwante producten** niet worden weergegeven op een Adobe Commerce-winkel. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd. De patch-id is MDVA-29787.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce op cloudinfrastructuur 2.3.3.

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.0.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De doelregel voor **Verwante producten** werkt niet wanneer &quot;*is een van*&quot; voorwaarde wordt gebruikt voor **Te tonen producten** in de Commerce Admin.

>[!NOTE]
>
>Opmerking: deze patch herstelt geen bestaande doelregels. U moet bestaande doelregels opnieuw creëren.

<u>Stappen om te reproduceren</u>:

1. Maken **Nieuw kenmerk** (Voorbeeld: Testen\_Attr).
   * Set **Invoertype catalogus voor winkeleigenaar** = *Tekst.*
   * In **Eigenschappen van Storefront**, set **Voorwaarden voor promotieregels gebruiken** = *Ja*.
1. Maken **Nieuwe kenmerkset** (Voorbeeld: Testen\_Set).
1. Voeg de **Nieuw kenmerk** aan de **Nieuwe kenmerkset** (Voorbeeld: &quot;Test\_Attr&quot;-kenmerk toevoegen aan de kenmerkset &quot;Test\_Set&quot;).
1. Maak drie producten. Deze zijn bijvoorbeeld als volgt ingesteld:
   * Product1, test\_Attr = MAGT2NA\_Test3
   * Product2, Testen\_Attr = 24-MB02
   * Product3, Test\_Attr = 701644329389M
1. Doel maken **Regel** (**Marketing**   > **Regels voor verwante producten** en klik op de knop **Regel toevoegen** knop.) met instellingen:
   * **Toepassen op** = *Verwante producten*
   * **Producten afstemmen**
   * Het nieuwe kenmerk dat u hebt gemaakt instellen **in** **Stap 1 hierboven** om het kenmerk Product1 te zijn (Voorbeeld: Test\_Attr = MAGT2NA\_Test3).
   * **Te tonen producten** = De kenmerken van de andere twee producten (Voorbeeld: 24-MB02- en 701644329389M-kenmerken).
1. Sla de **Regel**.
1. Voer indien nodig een nieuwe index uit.
1. Cache wissen.
1. Open Product1 op de voorzijde.

<u>Verwachte resultaten</u>:

De bijbehorende producten zijn aanwezig.

<u>Werkelijke resultaten</u>:

De verwante producten ontbreken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
