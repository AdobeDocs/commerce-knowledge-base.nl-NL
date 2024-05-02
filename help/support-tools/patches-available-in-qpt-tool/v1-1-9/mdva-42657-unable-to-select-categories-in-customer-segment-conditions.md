---
title: "MDVA-42657: Kan geen categorieën selecteren in de omstandigheden van het klantensegment"
description: Met de MDVA-42657-patch wordt het probleem opgelost waarbij de beheerder geen categorieën kan selecteren onder de voorwaarden van het klantensegment. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-42657. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 9c810dcd-b39b-4456-a362-5452ada4dc53
feature: Categories, Console, Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-42657: Kan geen categorieën selecteren in de omstandigheden van het klantensegment

Met de MDVA-42657-patch wordt het probleem opgelost waarbij de beheerder geen categorieën kan selecteren onder de voorwaarden van het klantensegment. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-42657. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruiker kan geen categorieën selecteren in de segmentvoorwaarden van de klant.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Klanten** > **Segmenten**.
1. Maak een nieuw segment.
1. Ga naar het nieuwe segment en klik op **Voorwaarden** in de linkerzijnavigatie.
1. Klik op het groene plusteken.
1. Selecteer Productgeschiedenis onder Producten.
1. Wijzig &#39;views&#39; in &#39;ordered&#39;.
1. &quot;ALL&quot; wijzigen in &quot;ANY&quot;.
1. Klik op het geneste groene plusteken en selecteer Categorie.
1. Klik op de knop **...** en klik vervolgens op het pictogram van de kiezer (links van het vinkje).
1. Open de browser Dev Console.
1. Controleer de selectievakjes voor om het even welke/veelvoudige categorieën en neem nota van de fout javascript die in de console wordt geworpen.
1. Klik op de knop **Opslaan** knop.
1. Navigeer terug naar de voorwaarde en controleer of de geselecteerde categorieën zijn opgeslagen.

<u>Verwachte resultaten</u>:

De geselecteerde categorieën worden opgeslagen en geselecteerd wanneer u de segmentvoorwaarden weergeeft/bewerkt.

<u>Werkelijke resultaten</u>:

De geselecteerde categorieën ontbreken en zijn niet goed opgeslagen. U krijgt de volgende fout in console:

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
