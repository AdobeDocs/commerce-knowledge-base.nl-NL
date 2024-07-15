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
Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 geïnstalleerd is. De patch-id is ACSD-44591. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker krijgt fouten wanneer hij of zij een bestelling probeert te plaatsen zonder CAPTCHA-bevestiging.

<u> Stappen om </u> te reproduceren:

1. Configureer Google ReCaptcha v2 (ik ben geen robot).
1. Enable ReCaptcha for checkout.
1. Probeer een bestelling te plaatsen zonder op de ReCaptcha te klikken.
1. Zodra u het foutenbericht voor het missen ReCaptcha (*ontbroken bevestiging ReCaptcha ontvangt, gelieve te proberen opnieuw*), op **ReCaptcha** te klikken en dan te proberen plaatsend een orde.

<u> Verwachte resultaten </u>:

De orde zal niet met onjuiste ReCaptcha worden geplaatst.

<u> Ware resultaten </u>:

U krijgt de volgende fouten:

* *Bevestiging ReCaptcha ontbrak, gelieve opnieuw te proberen*
* *Geen zulk karretje met identiteitskaart = 1*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
