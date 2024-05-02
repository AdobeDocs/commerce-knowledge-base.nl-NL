---
title: Adobe Commerce 2.4.1 en 2.3.6 maken een accountknop met uitgeschakelde hotfix
description: Dit artikel bevat een hotfix voor het probleem wanneer u moeite hebt om een nieuw account te maken nadat u een onjuiste waarde hebt ingevoerd in een veld op het formulier. Als u bijvoorbeeld een e-mailadres in de verkeerde notatie invoert of de velden voor de voornaam of achternaam leeg laat of geen waarde invoert die aan de wachtwoordvereisten voldoet. Een permanente oplossing wordt opgenomen in de Q1-releases (2.4.2, 2.4.1-p1 en 2.3.6-p1).
exl-id: e6e65ede-8156-4e2b-b369-b18395bb3dbf
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 en 2.3.6 maken een accountknop met uitgeschakelde hotfix

Dit artikel bevat een hotfix voor het probleem wanneer u moeite hebt om een nieuw account te maken nadat u een onjuiste waarde hebt ingevoerd in een veld op het formulier. Als u bijvoorbeeld een e-mailadres in de verkeerde notatie invoert of de velden voor de voornaam of achternaam leeg laat of geen waarde invoert die aan de wachtwoordvereisten voldoet. Een permanente oplossing wordt opgenomen in de Q1-releases (2.4.2, 2.4.1-p1 en 2.3.6-p1).

## Probleem

De **Een account maken** op de knop **Nieuw account maken** De pagina blijft uitgeschakeld als een klant ongeldige gegevens heeft ingevoerd. Zo voorkomt u dat kopers opnieuw proberen een account te maken nadat ze een fout hebben gemaakt.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Nieuwe klantaccount maken**.
1. Vul de formuliervelden in. In de **Wachtwoord** veld, invoerwaarden die niet voldoen aan de wachtwoordvereisten. Bijvoorbeeld:
   * De wachtwoorden in de **Wachtwoord** en de **Wachtwoord bevestigen** de velden komen niet overeen.
   * De wachtwoorden in de **Wachtwoord** en de **Wachtwoord bevestigen** de velden zijn niet lang genoeg .
1. Klik op de knop **Een account maken** knop.

<u>Verwachte resultaten</u>:

* **Een account maken** Deze knop moet actief blijven of ingeschakeld.
* De gebruiker moet een nieuwe account kunnen maken.

<u>Werkelijke resultaten</u>:

* **Een account maken** de knop blijft uitgeschakeld, zelfs nadat alle vereiste velden zijn ingevuld met geldige/correcte gegevens.
* De klant kan geen nieuwe account maken.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling: [MC-38509-composer.patch downloaden](assets/MC-38509-composer.patch.zip)

## Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce op wolkeninfrastructuur 2.3.6 en 2.4.1.
* Adobe Commerce op locatie 2.3.6 en 2.4.1.

De patch is niet compatibel met andere Adobe Commerce-versies en -versies.

## Hoe de pleister moet worden aangebracht

Zie [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies.

## Gerelateerde lezing

* [GitHub Adobe Commerce > Ongeldige verzendaccount aanmaken, zodat de verzendknop uitgeschakeld blijft](https://github.com/magento/magento2/issues/30513)
* [Adobe Commerce User Guide > Getting Started > Creating an Account](https://docs.magento.com/user-guide/magento/magento-account-create.html)
