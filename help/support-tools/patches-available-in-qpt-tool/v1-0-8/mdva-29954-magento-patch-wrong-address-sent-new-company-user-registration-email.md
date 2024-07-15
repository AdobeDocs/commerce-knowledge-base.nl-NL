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

De patch MDVA-29954 lost het probleem op waarbij de e-mails &quot;New Company Registration Request&quot; en &quot;You have been linked to a company&quot; via het onjuiste e-mailadres worden verzonden. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.5-p2, 2.4.0 en 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Eerste vereisten </u>:

Installeer Adobe Commerce met B2B, met **B2B Eigenschappen** en **toegelaten Bedrijf**.

<u> Stappen om </u> te reproduceren:

1. Klik op **creeer Rekening** dropdown op de storefront, en selecteer **creëren Nieuwe Rekening van het Bedrijf**.
1. Vul de vereiste velden in en registreer de account.
1. Laat het **Bedrijf** van het achtereind toe (**Klant** > **Bedrijven**).
1. Controleer het e-mailadres dat u voor registratie hebt gebruikt.
1. Plaats het **wachtwoord van Admin van het Bedrijf** door de gemailde instructies te volgen.
1. Login aan frontend met het **wachtwoord Admin van het Bedrijf**.
1. Creeer een nieuwe **Gebruiker van het Bedrijf** in **Mijn Rekening** > **Gebruikers van het Bedrijf** > **voeg Nieuwe Gebruiker** toe.
1. Ga naar **Opslag** > **Configuraties** > **e-mailadressen van de algemeen-Opslag** > **Algemene Contact**, en controleer **E-mail van de Afzender**.
1. Ga naar e-mail die u gebruikte om de **Nieuwe Gebruiker** in Stap 7 te registreren.

<u> Verwachte resultaten </u>:

&quot;U bent verbonden met een bedrijf&quot;e-mail verzonden van een e-mailadres met de zelfde waarde zoals voor **E-mail van de Afzender** in Stap 8.

<u> Ware resultaten </u>:

&quot;U bent verbonden met een bedrijf&quot;e-mail wordt verzonden van **Admin van Bedrijven** e-mail.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
