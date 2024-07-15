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

Dit artikel bevat een oplossing voor het geval dat een Commerce-beheerder een nieuwe gebruiker maakt met de beheerdersrechten en het wachtwoord als onbewerkte tekst wordt opgeslagen in de databasetabel van `magento_logging_event_changes` .

Installeer de beveiligingsupdate Adobe Commerce 2.0.16 en 2.1.9 om dit beveiligingsprobleem op te lossen. Nadat u de beveiligingsupdate hebt toegepast, worden de wachtwoorden versleuteld en worden ze niet als onbewerkte tekst weergegeven.

## Betrokken versies {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce op locatie 2.X.X
* Adobe Commerce op cloudinfrastructuur 2.X.X

## Probleem {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

Wanneer een bestaande Beheerder van Commerce tot een nieuwe gebruiker met de voorrechten van de Beheerder via **Systeem** **>** Toestemmingen **>** toevoegt nieuwe gebruiker **, wordt het wachtwoord (ingegaan als bevestiging) bewaard als gewone tekst in de `magento_logging_event_changes` gegevensbestandlijst.**

### Stappen om te reproduceren: {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. Login als Beheerder en creeer een nieuwe gebruiker door aan deze weg te navigeren: **Systeem** > Toestemmingen > **Alle Gebruikers**.

   ![ add_user_magento_2.4.1.png ](assets/add_user_magento_2.4.1.png)

1. Dan klik **toevoegen nieuwe gebruiker** pagina. Geef het wachtwoord van uw huidige beheerder op wanneer u hierom wordt gevraagd.
1. Ga naar het **Systeem** > **Logboek van de Actie** > **Rapport** pagina en vind de laatste logboekingang.
1. U kunt het huidige wachtwoord zien. Het wachtwoord is niet versleuteld of gehasht.

## Oplossing {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

Het installeren van [ Adobe Commerce 2.0.16 en 2.1.9 Update van de Veiligheid ](https://magento.com/security/patches/magento-2016-and-219-security-update) lost deze kwestie op.

Nadat u de beveiligingsupdate hebt geïnstalleerd, wordt het wachtwoord gecodeerd en wordt het niet weergegeven in onbewerkte tekst in de tabel `magento_logging_event_changes` .

## Meer informatie {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

[ Adobe Commerce 2.0.16 en 2.1.9 pagina van de Update van de Veiligheid ](https://magento.com/security/patches/magento-2016-and-219-security-update) in ons veiligheidscentrum.

[ bevorder de toepassing en de componenten van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) in onze ontwikkelaarsdocumentatie.
