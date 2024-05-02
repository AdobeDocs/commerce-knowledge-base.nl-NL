---
title: "ACSD-44591: fouten bij bestelling zonder CAPTCHA-bevestiging"
description: De ACSD-44591-patch lost het probleem op waarbij de gebruiker fouten krijgt bij het plaatsen van een bestelling zonder CAPTCHA-bevestiging.
exl-id: 5459aa14-dcba-474d-aafa-e4cc73daafbc
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-44591: fouten bij bestelling zonder CAPTCHA-bevestiging

De ACSD-44591-patch lost het probleem op waarbij de gebruiker fouten krijgt bij het plaatsen van een bestelling zonder CAPTCHA-bevestiging.
Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-44591. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker krijgt fouten wanneer hij of zij een bestelling probeert te plaatsen zonder CAPTCHA-bevestiging.

<u>Stappen om te reproduceren</u>:

1. Configureer Google ReCaptcha v2 (ik ben geen robot).
1. Enable ReCaptcha for checkout.
1. Probeer een bestelling te plaatsen zonder op de ReCaptcha te klikken.
1. Zodra u het foutbericht voor ontbrekende ReCaptcha ontvangt (*Validatie van reCaptcha mislukt. Probeer het opnieuw*), klikt u op **ReCaptcha** en probeer vervolgens een bestelling te plaatsen.

<u>Verwachte resultaten</u>:

De orde zal niet met onjuiste ReCaptcha worden geplaatst.

<u>Werkelijke resultaten</u>:

U krijgt de volgende fouten:

* *Validatie van reCaptcha mislukt. Probeer het opnieuw*
* *Karretje met id = 1*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
