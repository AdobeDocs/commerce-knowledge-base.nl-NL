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

De flard MDVA-35092 lost de kwestie op waar u Fout ziet: *&quot;Video niet Gevonden&quot;*. Dit foutbericht wordt weergegeven wanneer u een Vimeo-video invoert met de native interface Video toevoegen in de productbeheerder van Adobe Commerce. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.5 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De eenvoudige API van Vimeo werkt niet meer zoals verwacht.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de beheerder.
1. Om een bestaand product uit te geven, ga **CATALOGUS** Producten **>** uitgeven **, of om een nieuw product tot stand te brengen, ga** CATALOGUS **>** Producten **>** uitgeven **>** voeg Product **toe.**
1. Klik het **lusje van Beelden en van Video&#39;s** op de pagina van het Product.
1. Klik **toevoegen Video** en voeg URL van een video van Vimeo toe. Klik **sparen**.

<u> Verwachte resultaten </u>:

De nieuwe video wordt gevonden en opgeslagen.

<u> Ware resultaten </u>:

Fout: *&quot;Video niet Gevonden&quot;* wordt getoond.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
