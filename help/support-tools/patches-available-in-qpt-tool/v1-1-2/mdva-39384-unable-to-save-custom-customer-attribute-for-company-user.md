---
title: 'MDVA-39384: Kan aangepast kenmerk van klant niet opslaan voor zakelijke gebruiker'
description: De patch MDVA-39384 lost de kwestie op waar het attribuut van de douaneklant voor een bedrijfgebruiker niet wordt bewaard. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-39384. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: b9864ca6-307b-4649-b764-4512abc503d3
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# MDVA-39384: Onbekwaam om douanekenmerk van de klant voor bedrijfgebruiker te bewaren

De patch MDVA-39384 lost de kwestie op waar het attribuut van de douaneklant voor een bedrijfgebruiker niet wordt bewaard. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-39384. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aangepast klantkenmerk voor een bedrijfsgebruiker wordt niet opgeslagen.

<u>Vereisten</u>:

B2B-modules worden geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > Instellingen > **Configuratie** > **B2B-functies** en stelt de **Bedrijf inschakelen** op Ja.
1. Een aangepast klantkenmerk maken:
   * Vereiste waarden: Ja (optioneel, inschakelen zodat de validatiefout wordt weergegeven).
   * Tonen in winkelcentrum: Ja.
   * Forms to Use In: All available in the list.
1. Creeer een Bedrijf en login als bedrijfadmin.
1. Navigeer naar de bedrijfsstructuur in uw account.
1. Klik op de knop **Gebruiker toevoegen** koppeling.
1. Vul het formulier met het aangepaste kenmerk.
1. Klikken **Opslaan**.

<u>Verwachte resultaten</u>:

De waarden van de douanekenmerken worden bewaard met de nieuwe bedrijfgebruiker.

<u>Werkelijke resultaten</u>:

De waarden van de douanekenmerken worden NIET bewaard met de nieuwe bedrijfgebruiker.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
