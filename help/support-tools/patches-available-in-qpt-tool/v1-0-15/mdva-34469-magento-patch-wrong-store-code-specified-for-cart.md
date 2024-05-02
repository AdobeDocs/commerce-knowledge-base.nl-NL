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

Met de MDVA-34469-patch wordt het probleem opgelost waarbij gebruikers het foutbericht krijgen: *Onjuiste winkelcode opgegeven voor winkelwagentje* wanneer u een product aan de winkelwagentje toevoegt nadat u een andere winkelweergave hebt gekozen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 is geïnstalleerd. De patch-id is MDVA-34469. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker ziet een fout in de cartquery. *&quot;Onjuiste winkelcode opgegeven voor winkelwagentje&quot;*, wanneer u probeert om te schakelen tussen opslageweergaven.

<u>Vereisten</u>:

* Adobe Commerce 2.4.0.
* Eén website met één winkel en twee winkelweergaven zijn geconfigureerd.
* Er wordt een klantenaccount aangemaakt.

<u>Stappen om te reproduceren</u>:

1. Adobe Commerce backend is geconfigureerd voor twee winkelweergaven (met winkelcodes: standaard, tweede).
1. De gebruiker maakt een winkelwagentje met de standaardwinkelcode.
1. De gebruiker probeert deze winkelwagentje op te halen met de code van de tweede winkel in de `Store` aanvraagkoptekst.

<u>Verwachte resultaten</u>:

Het winkelwagentje wordt weergegeven omdat de winkel wordt verschoven (de nieuwe code wordt verzonden in de `Store` request header) associeert de winkelwagen met de gevraagde store.

<u>Werkelijke resultaten</u>:

De query retourneert een fout en de winkelwagentje wordt niet weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
