---
title: "ACSD-43887: onjuiste gegevens weergegeven op de betalingspagina voor afhandeling"
description: De ACSD-43887-patch verhelpt het probleem dat onjuiste gegevens worden weergegeven op de pagina voor afhandelingsuitkeringen wanneer Purchase Orders voor bedrijven zijn ingeschakeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-4387. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 07b17f96-5236-43a7-aeaf-6bfe36c551cf
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# ACSD-43887: onjuiste gegevens weergegeven op de betalingspagina voor afhandeling

De ACSD-43887-patch verhelpt het probleem dat onjuiste gegevens worden weergegeven op de pagina voor afhandelingsuitkeringen wanneer Purchase Orders voor bedrijven zijn ingeschakeld. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-4387. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er worden onjuiste gegevens weergegeven op de pagina voor de afhandeling van betalingen wanneer Aankooporders voor bedrijven zijn ingeschakeld.

<u>Vereisten</u>:

1. B2B-modules worden geïnstalleerd.
1. Bedrijf inschakelen is ingesteld op _Ja_. Ga naar **Winkels** > **Configuraties** > **Algemeen** > **B2B-functies** > **Bedrijf inschakelen** > **Ja**.
1. Inkooporders inschakelen is ingesteld op _Ja_. Ga naar **Goedkeuringsconfiguratie bestellen** > **Aankooporders inschakelen** > **Ja**.
1. PayPal Express is geconfigureerd als betalingsmethode.

<u>Stappen om te reproduceren</u>:

1. Maak een virtueel product.
1. Registreer een bedrijfsrekening van frontend met een bedrijf Admin.
1. Het bedrijfsaccount vanaf de back-end en set goedkeuren **Aankooporders inschakelen** als _Ja_ bij de goedkeuring van de onderneming.
1. Ga naar het front-end en login gebruikend de onderneming Admin rekening die in stap twee wordt gecreeerd.
1. Maak een standaardgebruiker voor het bedrijf. Ga naar **Bedrijfs gebruiker** > **Nieuwe gebruiker toevoegen**.
1. Maak een &#39;goedkeuringsregel&#39; voor het bedrijf. Ga naar **Goedkeuringsregels** > **Nieuwe regel toevoegen**.

   * Type regel: Totaal van volgorde
   * Totaal bestelling: is meer dan of gelijk aan $1
   * Goedkeuring vereist van: bedrijfsbeheerder

1. Meld u af en meld u aan met het account Standaardgebruiker.
1. Voeg het virtuele product dat in stap 1 is gemaakt toe aan de winkelwagentje en ga verder met het uitchecken.
1. Selecteer PayPal Express als betalingsmethode en klik op **Inkooporder plaatsen**.
1. Meld u af en meld u aan met de beheerdersaccount van het bedrijf.
1. Ga naar **Mijn inkooporders** en van **Zakelijke inkooporders**, klikt u op **Weergave** voor de volgorde die is gemaakt in stap negen.
1. Goedkeuren van de kooporder. De status van het inkooporderformulier moet &quot;Goedgekeurd: In afwachting van betaling&quot; zijn.
1. Meld u af en meld u aan met de account Standaard gebruiker van het bedrijf.
1. Ga naar **Mijn inkooporders** > **Weergave** > **Opdracht plaatsen**.
1. Controleer de **Overzicht van bestellingen**.

<u>Verwachte resultaten</u>:

In het orderoverzicht worden de juiste waarden voor niet-nul weergegeven.

<u>Werkelijke resultaten</u>:

De totale waarde van het orderoverzicht is nul.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
