---
title: 'MDVA-28661: probleem met het beheer van bedrijfsgebruikers bij het wijzigen van e-mailadressen voor beheerders'
description: De MDVA-28861-patch verhelpt het probleem waarbij de gebruikers een fout krijgen bij het wijzigen van het e-mailadres van de beheerder. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd. De patch-id is MDVA-28861.
exl-id: 2d6691e5-baaf-4cef-ae7e-2b6ccc7f2cd3
feature: Admin Workspace, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28661: probleem met beheer van bedrijfsgebruikers bij het wijzigen van e-mailadressen voor beheerders

De MDVA-28861-patch verhelpt het probleem waarbij de gebruikers een fout krijgen bij het wijzigen van het e-mailadres van de beheerder. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 geïnstalleerd is. De patch-id is MDVA-28861.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0 tot en met 2.4.1 (inclusief 2.3.5-p1) met B2B-uitbreiding

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Na het veranderen van het **e-mailadres van Admin van het Bedrijf** {, is een fout teruggekeerd, en de **lijst van de Gebruikers van het Bedrijf** wordt niet getoond.

<u> Stappen om </u> te reproduceren:

1. Laat de functionaliteit van het Bedrijf toe (leer meer over dat in [ installeer B2B: laat B2B eigenschappen in Commerce Admin ](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin) in onze ontwikkelaarsdocumentatie toe en creeer een nieuw Bedrijf met twee gebruikers - een admin en twee gebruikers - allen met e-mailadressen).
1. Ga naar **Commerce Admin** > **Klanten** > **Bedrijven** en open uw rekening van het Bedrijf.
1. Open **lusje Admin van het Bedrijf 1} en veranderings admin aan de eerste gebruiker, die het veranderen van** Admin van het Bedrijf **e-mail aan e-mail van de eerste gebruiker omvat.**
1. Ga naar de voorkant van de Adobe Commerce en meld u aan als de eerste gebruiker.
1. Ga naar de **sectie van de Gebruikers van het Bedrijf**.

<u> Verwachte resultaten </u>:

De **lijst van de Gebruikers van het Bedrijf** zou moeten worden getoond zoals verwacht.

<u> Ware resultaten </u>:

De **lijst van de Gebruikers van het Bedrijf** wordt niet getoond, en een fout gelijkend op de volgende vertoningen:

```bash
No such entity with id = 2
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.

Meer over de functionaliteit van het Bedrijf B2B leren, verwijs naar deze artikelen in onze ontwikkelaarsdocumentatie:

* [ B2B de Gids van de Ontwikkelaar ](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [ beheer bedrijfrollen ](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [ de configuratiewegen van de Uitbreiding van de Onderneming B2B van Adobe Commerce verwijzing ](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
