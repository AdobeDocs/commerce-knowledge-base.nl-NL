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

De patch MDVA-31007 lost het probleem op waar de attributen van het douaneadres niet correct worden getoond in de de detailpagina van de orde in het Mijn gebied van de Rekening en in het achterste eind (in **Verkoop > Bestellingen** locatie). Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de beheerder-back-end.
1. Navigeren naar **Winkels** > **Attributen** > **Adressen van klant**.
1. Twee kenmerken maken:

   * Invoertype instellen: *Vervolgkeuzelijst*.
   * Invoertype instellen: *Tekst*.

1. Navigeren naar **Winkels** > **Configuraties** > **Klant** > **Klantconfiguraties**.
1. Selecteren *Toepassingsgebied* als **Standaardwinkel** weergeven.
1. Breid uit **Adressjabloon** sectie. Bijwerken *Tekst*, *Tekst één regel*, en *HTML* om de twee bovenstaande aangepaste kenmerken op te nemen:

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. Open Storefront.
1. Maken en aanmelden met een gebruiker.
1. Ga naar **Mijn account** > **Adresboek** en voeg een nieuw adres toe (vul de twee aangepaste kenmerken in).
1. Voeg een product aan de kar toe, en plaats een orde.
1. Klik op de pagina met succesmeldingen voor bestellingen op **Volgnummer** koppeling.
1. Neem op de pagina met orderdetails de **Ordergegevens** sectie.
1. Ga naar **Achtergrond** > **Verkoop** > **Orders** klikt u op de bovenstaande volgorde en bekijkt de **Adresgegevens** sectie.

<u>Verwachte resultaten</u>:

Op zowel de voorzijde als de achterzijde worden het factuuradres en het verzendadres weergegeven zoals u had verwacht.

<u>Werkelijke resultaten</u>:

Op zowel voor- als achterkant wordt het factuuradres niet correct weergegeven. De geselecteerde optie van het drop-down attribuut ontbreekt, en de waarde van het inputattribuut bevat de attributencode.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
