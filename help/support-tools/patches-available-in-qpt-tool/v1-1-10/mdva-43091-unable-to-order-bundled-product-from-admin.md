---
title: "MDVA-43091: Kan gebundeld product niet bestellen bij Admin"
description: De MDVA-43091-patch lost het probleem op waarbij gebruikers geen gebundeld product kunnen bestellen bij de Commerce Admin. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-43091. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 77dff356-4f75-4b06-b62b-5379a4eec273
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-43091: Kan gebundeld product niet bestellen bij Admin

De MDVA-43091-patch lost het probleem op waarbij gebruikers geen gebundeld product kunnen bestellen bij de Commerce Admin. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 geïnstalleerd is. De patch-id is MDVA-43091. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het proberen om tot gebundeld product van Admin opdracht te geven, werpt het de volgende fout: *u kunt geen decimale hoeveelheid voor dit product gebruiken.*

<u> Stappen om </u> te reproduceren:

1. Een schone Adobe Commerce installeren.
1. Maak twee eenvoudige producten.
1. Maak een gebundeld product met twee opties.
1. Maak een klantenaccount op de voorzijde.
1. Ga naar **Admin** > **Verkoop** > **Orden** > **creeer Nieuwe Orde**.
   * Selecteer de klantenaccount die u zojuist hebt gemaakt.
   * Probeer het gebundelde product aan de kar toe te voegen.

<u> Verwachte resultaten </u>:

Admin-gebruiker kan het product met één hoeveelheid toevoegen aan het winkelwagentje.

<u> Ware resultaten </u>:

De gebruiker Admin krijgt de volgende fout: *u kunt decimale hoeveelheid voor dit product niet gebruiken.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
