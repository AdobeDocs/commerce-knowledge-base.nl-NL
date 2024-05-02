---
title: '''MDVA-35092: Vimeo Error: "Video not found"'
description: 'De patch MDVA-35092 verhelpt het probleem met Error: *"Video not Found"*. Dit foutbericht wordt weergegeven wanneer u een Vimeo-video invoert met de native interface Video toevoegen in de productbeheerder van Adobe Commerce. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd. Dit probleem is opgelost in Adobe Commerce 2.4.3. "'
exl-id: bc0952d9-1ea4-417c-926c-96875984d82c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# MDVA-35092: Vimeo-fout: &quot;Video niet gevonden&quot;

De patch MDVA-35092 verhelpt het probleem waarbij Error wordt weergegeven: *&quot;Video niet gevonden&quot;*. Dit foutbericht wordt weergegeven wanneer u een Vimeo-video invoert met de native interface Video toevoegen in de productbeheerder van Adobe Commerce. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.5 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De eenvoudige API van Vimeo werkt niet meer zoals verwacht.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de beheerder.
1. Ga naar als u een bestaand product wilt bewerken **CATALOGUS** > **Producten** > **Bewerken** of als u een nieuw product wilt maken, gaat u naar **CATALOGUS** > **Producten** > **Bewerken** > **Product toevoegen**.
1. Klik op de knop **Afbeeldingen en video&#39;s** op de productpagina.
1. Klikken **Video toevoegen** en voeg de URL van een Vimeo-video toe. Klikken **Opslaan**.

<u>Verwachte resultaten</u>:

De nieuwe video wordt gevonden en opgeslagen.

<u>Werkelijke resultaten</u>:

Fout: *&quot;Video niet gevonden&quot;* wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
