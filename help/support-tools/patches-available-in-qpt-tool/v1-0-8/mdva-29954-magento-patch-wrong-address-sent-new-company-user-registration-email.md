---
title: "MDVA-29954: onjuist adres heeft nieuwe e-mail voor de gebruikersregistratie van bedrijven verzonden"
description: De patch MDVA-29954 lost het probleem op waarbij de e-mails "New Company Registration Request" en "You have been linked to a company" via het onjuiste e-mailadres worden verzonden. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 9b3d1b93-3fe6-40a0-a68a-3e3d789c6d66
feature: B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29954: onjuist adres heeft nieuwe e-mail voor gebruikersregistratie van bedrijven verzonden

De patch MDVA-29954 lost het probleem op waarbij de e-mails &quot;New Company Registration Request&quot; en &quot;You have been linked to a company&quot; via het onjuiste e-mailadres worden verzonden. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.5-p2, 2.4.0 en 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Vereisten</u>:

Installeer Adobe Commerce met B2B, met **B2B-functies** en **Bedrijf** ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Klik op de knop **Account maken** vervolgkeuzelijst op de winkel en selecteer **Nieuw bedrijfsaccount maken**.
1. Vul de vereiste velden in en registreer de account.
1. De optie **Bedrijf** vanaf de achtergrond (**Klant** > **Bedrijven**).
1. Controleer het e-mailadres dat u voor registratie hebt gebruikt.
1. Stel de **Bedrijfsbeheerderswachtwoord** door de e-mailinstructies te volgen.
1. Meld u aan bij de voorzijde met de **Bedrijfsbeheerderswachtwoord**.
1. Een nieuwe **Bedrijfs gebruiker** in **Mijn account** > **Bedrijfsgebruikers** > **Nieuwe gebruiker toevoegen**.
1. Ga naar **Winkels** > **Configuraties** > **E-mailadressen voor algemene opslag** > **Algemene contactpersoon** en controleren **E-mail afzender**.
1. Ga naar de e-mail die u hebt gebruikt om de **Nieuwe gebruiker** in Stap 7.

<u>Verwachte resultaten</u>:

Het e-mailadres &#39;Je bent gekoppeld aan een bedrijf&#39; wordt verzonden van een e-mailadres met dezelfde waarde als voor de **E-mail afzender** in Stap 8.

<u>Werkelijke resultaten</u>:

De e-mail &quot;Je bent gekoppeld aan een bedrijf&quot; wordt verzonden vanuit de **Ondernemingsbeheerder** e-mail.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
