---
title: Wachtwoorden voor beheerders die zijn opgeslagen als onbewerkte tekst in het logboek Handelingen
description: Dit artikel verstrekt een moeilijke situatie voor wanneer een Beheerder van Commerce tot een nieuwe gebruiker met de voorrechten van de Beheerder leidt en het wachtwoord wordt bewaard als gewone tekst in de ` magento_logging_event_changes' gegevensbestandlijst.
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Wachtwoorden voor beheerders die zijn opgeslagen als onbewerkte tekst in het logboek Handelingen

Dit artikel bevat een oplossing voor het geval dat een Commerce-beheerder een nieuwe gebruiker maakt met de beheerdersrechten en het wachtwoord als onbewerkte tekst wordt opgeslagen in het dialoogvenster `magento_logging_event_changes` databasetabel.

Installeer de beveiligingsupdate Adobe Commerce 2.0.16 en 2.1.9 om dit beveiligingsprobleem op te lossen. Nadat u de beveiligingsupdate hebt toegepast, worden de wachtwoorden versleuteld en worden ze niet als onbewerkte tekst weergegeven.

## Betrokken versies {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce op locatie 2.X.X
* Adobe Commerce op cloudinfrastructuur 2.X.X

## Probleem {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

Als een bestaande Commerce Administrator een nieuwe gebruiker maakt met de beheerdersrechten via **Systeem** > **Machtigingen** > **Alle gebruikers** > **Nieuwe gebruiker toevoegen**, wordt het wachtwoord (ingevoerd als bevestiging) opgeslagen als onbewerkte tekst in het dialoogvenster `magento_logging_event_changes` databasetabel.

### Stappen om te reproduceren: {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. Meld u aan als beheerder en maak een nieuwe gebruiker door naar dit pad te navigeren: **Systeem** > Machtigingen > **Alle gebruikers**.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. Klik vervolgens op de knop **Nieuwe gebruiker toevoegen** pagina. Geef het wachtwoord van uw huidige beheerder op wanneer u hierom wordt gevraagd.
1. Ga naar de **Systeem** > **Handelingenlogboek** > **Rapport** en zoek naar de laatste logbestandvermelding.
1. U kunt het huidige wachtwoord zien. Het wachtwoord is niet versleuteld of gehasht.

## Oplossing {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

De installatie van de [Adobe Commerce 2.0.16- en 2.1.9-beveiligingsupdate](https://magento.com/security/patches/magento-2016-and-219-security-update) verhelpt dit probleem.

Nadat u de beveiligingsupdate hebt geïnstalleerd, wordt het wachtwoord gecodeerd en wordt het niet weergegeven in onbewerkte tekst in het dialoogvenster `magento_logging_event_changes` tabel.

## Meer informatie {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

[Adobe Commerce 2.0.16 en 2.1.9 pagina Beveiligingsupdate](https://magento.com/security/patches/magento-2016-and-219-security-update) in ons veiligheidscentrum.

[Een upgrade uitvoeren van de Adobe Commerce-toepassing en -onderdelen](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) in onze ontwikkelaarsdocumentatie.
