---
title: 'MDVA-38799: Downloadbare producten die niet zijn opgeslagen na het maken van een gefaseerde update'
description: Met de MDVA-38799-patch wordt het probleem opgelost waarbij downloadbare producten niet worden opgeslagen na het maken van een testupdate. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 is geïnstalleerd. De patch-id is MDVA-38799. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: 306f9ef3-ca3a-41b9-a5d3-42aa4ef59953
feature: Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-38799: Downloadbare producten die niet zijn opgeslagen na het maken van een testupdate

Met de MDVA-38799-patch wordt het probleem opgelost waarbij downloadbare producten niet worden opgeslagen na het maken van een testupdate. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 is geïnstalleerd. De patch-id is MDVA-38799. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Downloadbare producten worden niet opgeslagen nadat een testupdate is gemaakt. Gebruikers krijgen het foutbericht: *Het downloadbare voorbeeld is niet gerelateerd aan het product. De koppeling controleren en het opnieuw proberen*.

<u>Stappen om te reproduceren</u>:

1. Navigeren naar **Catalogus** > **Producten**.
1. Klik op het vervolgkeuzemenu naast Product toevoegen en selecteer Downloadbaar product.
   * Vul de naam, SKU, prijs en hoeveelheid van het product in.
1. Blader omlaag naar de pagina Downloadbare gegevens.
1. Klik onder Voorbeelden op **Koppeling toevoegen**.
   * Vul de Titel in, Bestand uploaden (het bestandstype is niet van belang).
1. Klikken **Opslaan**. U krijgt het volgende bericht: *U hebt het product opgeslagen*.
1. Klikken **Nieuwe update plannen** boven aan de pagina.
   * Vul de Naam van de Update en een wettige Datum van het Begin en van het Eind in.
1. Klikken **Opslaan** in de testupdate.
1. Klikken **Opslaan** op het product.

<u>Verwachte resultaten</u>:

Het product wordt zonder fout opgeslagen.

<u>Werkelijke resultaten</u>:

U krijgt het foutbericht: *Het downloadbare voorbeeld is niet gerelateerd aan het product. De koppeling controleren en het opnieuw proberen*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
