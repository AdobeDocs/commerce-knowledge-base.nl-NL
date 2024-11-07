---
title: "ACSD-43887: onjuiste gegevens weergegeven op de betalingspagina voor afhandeling"
description: De ACSD-43887-patch verhelpt het probleem dat onjuiste gegevens worden weergegeven op de pagina voor afhandelingsuitkeringen wanneer Purchase Orders voor bedrijven zijn ingeschakeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-4387. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 07b17f96-5236-43a7-aeaf-6bfe36c551cf
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# ACSD-43887: onjuiste gegevens weergegeven op de betalingspagina voor afhandeling

De ACSD-43887-patch verhelpt het probleem dat onjuiste gegevens worden weergegeven op de pagina voor afhandelingsuitkeringen wanneer Purchase Orders voor bedrijven zijn ingeschakeld. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 geïnstalleerd is. De patch-id is ACSD-4387. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er worden onjuiste gegevens weergegeven op de pagina voor de afhandeling van betalingen wanneer Aankooporders voor bedrijven zijn ingeschakeld.

<u> Eerste vereisten </u>:

1. B2B-modules worden geïnstalleerd.
1. Laat Bedrijf toe wordt geplaatst aan _ja_. Ga naar **Opslag** > **Configuraties** > **Algemeen** > **Eigenschappen B2B** > **laat Bedrijf** toe > **ja**.
1. Laat Inkooporders toe wordt geplaatst aan _ja_. Ga naar **de Configuratie van de Goedkeuring van de Orde** > **toelaten de Orden van de Aankoop** > **ja**.
1. PayPal Express is geconfigureerd als betalingsmethode.

<u> Stappen om </u> te reproduceren:

1. Maak een virtueel product.
1. Registreer een bedrijfsrekening van frontend met een bedrijf Admin.
1. Goedkeuren de bedrijfrekening van de achterste en reeks **laat de Orden van de Aankoop** als _toe ja_ terwijl het goedkeuren van het bedrijf.
1. Ga naar het front-end en login gebruikend de onderneming Admin rekening die in stap twee wordt gecreeerd.
1. Maak een standaardgebruiker voor het bedrijf. Ga naar **Gebruiker van het Bedrijf** > **Nieuwe Gebruiker** toevoegen.
1. Maak een &#39;goedkeuringsregel&#39; voor het bedrijf. Ga naar **Regels van de Goedkeuring** > **Nieuwe Regel** toevoegen.

   * Type regel: Totaal van volgorde
   * Totaal bestelling: is meer dan of gelijk aan $1
   * Goedkeuring vereist van: bedrijfsbeheerder

1. Meld u af en meld u aan met het account Standaardgebruiker.
1. Voeg het virtuele product dat in stap 1 is gemaakt toe aan de winkelwagentje en ga verder met het uitchecken.
1. Selecteer Uitdrukkelijke PayPal als betalingsmethode en klik op **de Orde van de Aankoop van de Plaats**.
1. Meld u af en meld u aan met de beheerdersaccount van het bedrijf.
1. Ga naar **Mijn Orden van de Aankoop** en van **de Orden van de Aankoop van het Bedrijf**, klik op **Mening** voor de orde die in stap negen wordt gecreeerd.
1. Goedkeuren van de kooporder. De status van het inkooporderformulier moet &quot;Goedgekeurd: In afwachting van betaling&quot; zijn.
1. Meld u af en meld u aan met de account Standaard gebruiker van het bedrijf.
1. Ga naar **Mijn Orden van de Aankoop** > **Mening** > **Orde van de Plaats**.
1. Controleer het **Samenvatting van de Orde**.

<u> Verwachte resultaten </u>:

In het orderoverzicht worden de juiste waarden voor niet-nul weergegeven.

<u> Ware resultaten </u>:

De totale waarde van het orderoverzicht is nul.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
