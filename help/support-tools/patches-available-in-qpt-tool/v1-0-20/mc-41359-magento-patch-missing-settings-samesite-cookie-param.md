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

De MC-41359 handelspatch verhelpt de kwestie met ontbrekende montages van de de koekjesparameters van SameSite. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MC-41359. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.4.2

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.6-p1, 2.4.2, 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Ontbrekende instellingen van de SameSite cookie parameter.

<u>Stappen om te reproduceren:</u>

Vereisten:

* Chrome openen en naar chrome://flags/ gaan
* Inschakelen **ZelfdeSite, standaard cookies** en **Cookies zonder SameSite moeten beveiligd zijn**.
* Open de Chrome-controle.

<u>Scenario 1</u>

1. Enable PayPal.
1. Ga naar de winkel voor.
1. Voeg een product toe aan de kar.
1. Ga naar Afrekenen.

<u>Scenario 2</u>

Als u New Relic hebt [enabled](https://docs.magento.com/user-guide/reports/new-relic-reporting.html) de waarschuwing verschijnt op om het even welke voorste pagina.

<u>Werkelijk resultaat:</u>

Waarschuwingsbericht in de browserconsole: *Een cookie die aan een bron voor meerdere sites is gekoppeld, is zonder een SameSite-kenmerk ingesteld.*

<u>Verwacht resultaat:</u>

&quot;lax&quot; mag niet aan het cookiedomein worden toegevoegd; hetzelfde kenmerk moet aanwezig zijn met de standaardwaarde.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in het gereedschap QPT, raadpleegt u [Reparaties beschikbaar in het gereedschap QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
