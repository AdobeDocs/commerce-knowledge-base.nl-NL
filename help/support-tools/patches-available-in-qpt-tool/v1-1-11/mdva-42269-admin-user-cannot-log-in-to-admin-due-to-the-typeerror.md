---
title: '''MDVA-42269: Admin user cannot log into Admin due to the "TypeError" error'
description: De MDVA-42269-patch verhelpt het probleem waarbij Admin-gebruikers zich vanwege TypeError niet kunnen aanmelden bij Admin. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 is geïnstalleerd.  De patch-id is MDVA-42269.  De meest recente patchupdate vindt u in QPT 1.1.15. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 66d744a2-054e-493c-a060-9ed78447e35b
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42269: Admin-gebruiker kan zich niet aanmelden bij Admin vanwege de fout TypeError

De MDVA-42269-patch verhelpt het probleem waarbij Admin-gebruikers zich vanwege TypeError niet kunnen aanmelden bij Admin. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 is geïnstalleerd.  De patch-id is MDVA-42269.  De meest recente patchupdate vindt u in QPT 1.1.15. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1, 2.3.7-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1 - 2.4.3-p2, 2.3.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beheerders kunnen zich niet aanmelden bij de beheerder vanwege de volgende fout: *TypeError: strtotime() verwacht dat parameter 1 een tekenreeks is, met de waarde null.*

<u>Stappen om te reproduceren</u>:

Meld u aan bij de Commerce-beheerder.

<u>Verwachte resultaten</u>:

De beheerder kan zich aanmelden met de juiste gebruikersnaam en het juiste wachtwoord.

<u>Werkelijke resultaten</u>:

De beheerder kan zich niet aanmelden. De volgende fout wordt geregistreerd: *TypeError: strtotime() verwacht dat parameter 1 een tekenreeks is, met de waarde null.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
