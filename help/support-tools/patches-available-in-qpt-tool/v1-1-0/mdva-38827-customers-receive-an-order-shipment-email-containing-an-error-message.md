---
title: 'MDVA-38827: Klanten ontvangen per e-mail een fout bij het verzenden van orders'
description: 'De MDVA-38827-patch verhelpt het probleem dat klanten een e-mail met een bestelling ontvangen met het volgende foutbericht: *Er is helaas een fout opgetreden bij het genereren van deze inhoud*. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.0 is geïnstalleerd. De patch-id is MDVA-38827. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.'
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827: Klanten ontvangen per e-mail een fout bij het verzenden van orders

Het flard MDVA-38827 lost de kwestie op waar de klanten een e-mail van de ordeverzending die het volgende foutenbericht bevatten ontvangen: *wij spijt, is een fout voorgekomen terwijl het produceren van deze inhoud*. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.0 geïnstalleerd is. De patch-id is MDVA-38827. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer de Notify Klanten door de optie E-mail voor verzending wordt geselecteerd, ontvangen de klanten een e-mail die het volgende foutenbericht bevat: *wij spijt, is een fout voorgekomen terwijl het produceren van deze inhoud*.

<u> Stappen om </u> te reproduceren:

1. Ga naar **de Marketing** > **Mededelingen** > **E-mailMalplaatjes** en selecteer **Nieuw Malplaatje** toevoegen.
   * Selecteer **de Verkoop van het Magento 0&rbrace;** Nieuwe Verzending **.**
   * Klik op **Malplaatje van de Lading**.
   * Voeg een malplaatjenaam (b.v., de Verzendmalplaatje van de Kern) toe en klik **sparen**.
1. Ga naar **Opslag** > Montages > **Configuratie** > **Verkoop** > **E-mail van de Verkoop**:
   * Laat **Commentaren van de Verzending** toe.
   * Selecteer **Sjabloon van de Verzending van de Kern** (verwijs naar het &quot;voeg een malplaatjenaam&quot;deel van Stap 1 toe) onder E-mailMalplaatje van de Commentaar van de Commentaar van de Verzending en E-mailMalplaatje van de Commentaar van de Verzending voor Gast.
1. Plaats een bestelling. Ga naar het Admin paneel > **Verkoop** > **Orde**, klik **Mening**, en verzend dan de orde.
1. De ordestatus verandert van In behandeling in Verwerking.
1. Klik **Verzendingen** op het linkerzijbalkmenu en klik dan **Mening** om de orde te zien.
1. Voeg een commentaar in **Tekst van de Commentaar** hieronder **Verzendgeschiedenis** toe en controleer checkbox **Klant door E-mail** op de hoogte brengen.
1. Klik **voorleggen Commentaar**.

<u> Verwachte resultaten </u>:

Verkoop-e-mail met opmerkingen bij verzending wordt gegenereerd.

<u> Ware resultaten </u>:

Het volgende foutenbericht wordt ontvangen in e-mail: *wij spijt, is een fout voorgekomen terwijl het produceren van deze inhoud.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
