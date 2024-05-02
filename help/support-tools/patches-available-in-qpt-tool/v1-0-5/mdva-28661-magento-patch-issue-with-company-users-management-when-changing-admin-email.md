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

De MDVA-28861-patch verhelpt het probleem waarbij de gebruikers een fout krijgen bij het wijzigen van het e-mailadres van de beheerder. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd. De patch-id is MDVA-28861.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0 tot en met 2.4.1 (inclusief 2.3.5-p1) met B2B-uitbreiding

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Nadat u de **Bedrijfsbeheerder** e-mailadres, een fout wordt geretourneerd en de **Bedrijfsgebruikers** wordt niet weergegeven.

<u>Stappen om te reproduceren</u>:

1. Bedrijffunctionaliteit inschakelen (meer informatie hierover vindt u in [B2B installeren: B2B-functies inschakelen in Commerce Admin](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin) in onze ontwikkelaarsdocumentatie en creeer een nieuw Bedrijf met twee gebruikers - een admin en twee gebruikers - allen met e-mailadressen).
1. Ga naar de **Commerce Admin** > **Klanten** > **Bedrijven** en opent u uw bedrijfsaccount.
1. Openen **Bedrijfsbeheerder** tab en wijzig de beheerder in de eerste gebruiker, waaronder het wijzigen van de **Bedrijfsbeheerder** e-mail naar de e-mail van de eerste gebruiker.
1. Ga naar de voorkant van de Adobe Commerce en meld u aan als de eerste gebruiker.
1. Ga naar de **Bedrijfsgebruikers** sectie.

<u>Verwachte resultaten</u>:

De **Bedrijfsgebruikers** lijst moet worden weergegeven zoals u verwacht.

<u>Werkelijke resultaten</u>:

De **Bedrijfsgebruikers** wordt niet weergegeven en er wordt een fout weergegeven die lijkt op de volgende:

```bash
No such entity with id = 2
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.

Meer over de functionaliteit van het Bedrijf B2B leren, verwijs naar deze artikelen in onze ontwikkelaarsdocumentatie:

* [B2B-ontwikkelaarsgids](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Bedrijfsrollen beheren](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Referentie voor configuratiepaden voor Adobe Commerce Enterprise B2B-extensies](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
