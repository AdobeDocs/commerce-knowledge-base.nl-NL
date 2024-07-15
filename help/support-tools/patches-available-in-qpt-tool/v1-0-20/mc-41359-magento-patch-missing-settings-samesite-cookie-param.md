---
title: 'MC-41359 commercepatroon: ontbrekende instellingen SameSite cookie param'
description: De MC-41359 handelspatch verhelpt de kwestie met ontbrekende montages van de de koekjesparameters van SameSite. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MC-41359. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: b48faa3f-0d9a-4d65-9abb-1573c6240635
feature: Observability
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# MC-41359 commercepatroon: ontbrekende instellingen SameSite cookie param

De MC-41359 handelspatch verhelpt de kwestie met ontbrekende montages van de de koekjesparameters van SameSite. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 geïnstalleerd is. De patch-id is MC-41359. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.4.2

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op-gebouw en Adobe Commerce op wolkeninfrastructuur 2.3.6-p1, 2.4.2, 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Ontbrekende instellingen van de SameSite cookie parameter.

<u> Stappen om te reproduceren:</u>

Vereisten:

* Open Chrome en ga naar chrome://flags/
* Laat **SameSite door standaardkoekjes** toe en **Cookies zonder SameSite moet veilig** zijn.
* Open de Chrome-controle.

<u> Scenario 1:</u>

1. Enable PayPal.
1. Ga naar de winkel voor.
1. Voeg een product toe aan de kar.
1. Ga naar Afrekenen.

<u> Scenario 2:</u>

Als u New Relic [ ](https://docs.magento.com/user-guide/reports/new-relic-reporting.html) toegelaten hebt verschijnt de waarschuwing op om het even welke voorste pagina.

<u> Ware resultaat:</u>

Het bericht van de waarschuwing in de browser console: *een koekje verbonden aan een dwars-plaatsmiddel werd geplaatst zonder een attribuut SameSite.*

<u> Verwacht resultaat:</u>

&quot;lax&quot; mag niet aan het cookiedomein worden toegevoegd; hetzelfde kenmerk moet aanwezig zijn met de standaardwaarde.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > passen flarden ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelingsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar [ Vlekken beschikbaar in hulpmiddel QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
