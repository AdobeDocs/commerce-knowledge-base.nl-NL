---
title: 'ACSD-46703: slepen en neerzetten van producten werkt niet'
description: Dit artikel biedt een oplossing voor het probleem waarbij slepen en neerzetten van de aanpasbare opties van het product niet naar behoren werkt.
exl-id: 49b29495-d225-4f34-ac76-b7294a86aea6
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-46703: slepen en neerzetten van producten werkt niet

De ACSD-46703-patch verhelpt het probleem waarbij de aanpasbare opties (slepen en neerzetten) van het product niet naar behoren werken. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 is geïnstalleerd. De patch-id is ACSD-46703. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [Gereedschap Kwaliteitspatches] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen de aanpasbare opties niet van de ene pagina naar de andere slepen.

<u>Stappen om te reproduceren</u>:

1. Maak een eenvoudig product.
1. Voeg aanpasbare opties toe aan het eenvoudige product en zorg ervoor dat u meer dan 20 opties toevoegt die resulteren in paginering.
1. Probeer een aanpasbare optie (slepen en neerzetten) op dezelfde pagina te plaatsen.
1. Verplaats nu een aanpasbare optie van pagina twee naar pagina één.

<u>Verwachte resultaten</u>:

* U kunt de aanpasbare opties van de ene pagina naar de andere slepen.
* U kunt de waarden sorteren met slepen en neerzetten, zelfs voor meerdere pagina&#39;s.

<u>Werkelijke resultaten</u>:

U kunt geen waarde naar een andere pagina verplaatsen met de functie slepen en neerzetten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding voor het gereedschap Kwaliteitspatches.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de handleiding voor het gereedschap Kwaliteitspatches.
