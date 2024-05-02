---
title: "MDVA-31242: afgifte in CSV-formaat bij uitvoer"
description: Met de MDVA-31242-patch wordt het probleem opgelost waarbij een fout optreedt bij het exporteren van orders in CSV-bestandsindeling. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 1e343f23-5b10-492b-885f-8113ace4777f
feature: B2B, Data Import/Export, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# MDVA-31242: afgifte in CSV-formaat bij uitvoer

Met de MDVA-31242-patch wordt het probleem opgelost waarbij een fout optreedt bij het exporteren van orders in CSV-bestandsindeling. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (implementatiemethoden) 2.3.0 - 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de beheerder-back-end.
1. Inschakelen **Bedrijf** om **Winkels** > **Configuratie** > **B2B-functies**.
1. Ga naar **Verkoop** > **Orders**.
1. Klik op de knop **Kolom** > **Bedrijfsnaam** selectievakje.
1. Geef een waarde op in het dialoogvenster **Filters** > **Bedrijfsnaam** tekstveld.
1. Klik op de knop **Filters toepassen** knop.
1. Klik op de knop **Exporteren** > **CSV** > **Exporteren** knop.

<u>Verwachte resultaten</u>:

Het geselecteerde bestand wordt geopend zoals u had verwacht.

<u>Werkelijke resultaten</u>:

Wit scherm met de fout *Er is een fout opgetreden bij het verwerken van uw verzoek* wordt de uitzondering weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
