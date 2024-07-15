---
title: "MDVA-34469: Onjuiste winkelcode voor winkelwagentje"
description: '''De MDVA-34469-patch lost het probleem op waarbij gebruikers het foutbericht krijgen: *Onjuiste winkelcode opgegeven voor winkelwagentje* wanneer een product aan het winkelwagentje wordt toegevoegd na het schakelen van de winkelweergaven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 is geïnstalleerd. De patch-id is MDVA-34469. Dit probleem is opgelost in Adobe Commerce 2.4.2. "'
exl-id: 35d4f120-7fcf-4996-8b23-aca99cfc18ac
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-34469: Onjuiste winkelcode voor winkelwagentje

Het flard MDVA-34469 lost de kwestie op waar de gebruikers het foutenbericht krijgen: *Verkeerde opslagcode die voor kar* wordt gespecificeerd wanneer het toevoegen van een product aan de kar na de meningen van de omschakelingsopslag. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 geïnstalleerd is. De patch-id is MDVA-34469. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker ziet een fout van de wortelvraag, *&quot;Verkeerde opslagcode die voor winkelwagentje&quot;wordt gespecificeerd*, wanneer het proberen om opslagmeningen te schakelen.

<u> Eerste vereisten </u>:

* Adobe Commerce 2.4.0.
* Eén website met één winkel en twee winkelweergaven zijn geconfigureerd.
* Er wordt een klantenaccount aangemaakt.

<u> Stappen om </u> te reproduceren:

1. Adobe Commerce backend is geconfigureerd voor twee winkelweergaven (met winkelcodes: standaard, tweede).
1. De gebruiker maakt een winkelwagentje met de standaardwinkelcode.
1. De gebruiker probeert dit winkelwagentje op te halen met de code van de tweede winkel in de aanvraagheader van `Store` .

<u> Verwachte resultaten </u>:

Het winkelwagentje wordt weergegeven omdat het winkelwagentje (dat de nieuwe code verzendt in de `Store` aanvraagheader) wordt gekoppeld aan het winkelwagentje.

<u> Ware resultaten </u>:

De query retourneert een fout en de winkelwagentje wordt niet weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
