---
title: 'MDVA-39305: Aanmeldingsprobleem met ingeschakelde Google reCAPTCHA'
description: De MDVA-39305-patch verhelpt het probleem dat geregistreerde klanten zich niet kunnen aanmelden met de ingeschakelde Google reCAPTCHA. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 is geïnstalleerd. De patch-id is MDVA-39305. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.4 en 2.4.7.
exl-id: 1e8e7dc7-f8f1-4432-90f4-dc73d85f353a
feature: Console
role: Admin
source-git-commit: d48abbf3ecc19a78ee1d86a12d9c32cba17d53e5
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-39305: Aanmeldingsprobleem met ingeschakelde Google reCAPTCHA

De MDVA-39305-patch verhelpt het probleem dat geregistreerde klanten zich niet kunnen aanmelden met de ingeschakelde Google reCAPTCHA. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 is geïnstalleerd. De patch-id is MDVA-39305. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.4 en 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce on cloud Infrastructure 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Geregistreerde klanten kunnen zich niet aanmelden met de ingeschakelde Google reCAPTCHA.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkel** > **Configuratie** > **Beveiliging** > **Google reCAPTCHA Storefront** en **Google reCAPTCHA**.
1. Ga naar **Frontend**.
1. Openen **Console voor ontwikkelaars** in de browser.

<u>Verwachte resultaten</u>:

Geen CSP waarschuwingen in de console.

<u>Werkelijke resultaten</u>:

CSP waarschuwingen in de console.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
