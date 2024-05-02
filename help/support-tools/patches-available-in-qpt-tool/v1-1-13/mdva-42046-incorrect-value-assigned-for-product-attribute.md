---
title: "MDVA-42046: Onjuiste waarde toegewezen voor productkenmerk"
description: De patch MDVA-42046 verhelpt het probleem waarbij een onjuiste waarde wordt toegewezen aan het kenmerk product bij het bijwerken van een product met een invoerveld voor de datum. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-42046. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 837f5582-849c-43a3-ae02-87f71fb96061
feature: Attributes, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-42046: Onjuiste waarde toegewezen voor productkenmerk

De patch MDVA-42046 verhelpt het probleem waarbij een onjuiste waarde wordt toegewezen aan het kenmerk product bij het bijwerken van een product met een invoerveld voor de datum. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-42046. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.3.5-p2 en 2.4.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Nadat u een product hebt opgeslagen met `news_from_date` en/of `news_to_date` velden, worden de waarden van deze velden opnieuw ingesteld op de standaardwaarde.

<u>Stappen om te reproduceren</u>:

1. Maak een eenvoudig product.
1. Exporteer het product dat in stap 1 is gemaakt.
1. Plaats in het geëxporteerde CSV-bestand enkele waarden in het dialoogvenster `news_from_date` en `news_to_date` velden. Bijvoorbeeld 2021-05-15 en 2021-06-18.
1. Importeer het product met het gewijzigde CSV-bestand.
1. Voeg aanvullende kolommen &quot;Product instellen als nieuw vanaf datum&quot; en &quot;Product instellen als nieuw op datum&quot; toe aan het productraster.
1. Open de bewerkingspagina voor het product en klik zonder wijzigingen op **Opslaan**.
1. Ga terug naar het productraster en controleer de gegevens voor het product.

<u>Verwachte resultaten</u>:

Zowel &#39;Product instellen als Nieuw vanaf datum&#39; als &#39;Product instellen als Nieuw op datum&#39; zijn hetzelfde als vóór opslaan.

<u>Werkelijke resultaten</u>:

* De waarden in de kolommen &quot;Product instellen als nieuw vanaf datum&quot; en &quot;Product instellen als nieuw op datum&quot; worden gewijzigd.

* De kolom &quot;Product instellen als nieuw op datum&quot; toont de huidige datum en de kolom &quot;Product instellen als nieuw op datum&quot; is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
