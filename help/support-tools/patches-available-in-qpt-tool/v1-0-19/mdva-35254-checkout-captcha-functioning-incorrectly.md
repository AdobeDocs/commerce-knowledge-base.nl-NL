---
title: "MDVA-35254: Uitchecken CAPTCHA functioneert onjuist"
description: De patch MDVA-35254 verhelpt het probleem met CAPTCHA-velden die niet worden weergegeven na een ongeslaagd aantal pogingen tot afhandeling voor betaling door derden. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35254. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: 226c672b-3740-4a87-9ea1-66892acb9fe2
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-35254: Uitchecken CAPTCHA functioneert onjuist

De patch MDVA-35254 verhelpt het probleem met CAPTCHA-velden die niet worden weergegeven na een ongeslaagd aantal pogingen tot afhandeling voor betaling door derden. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 geïnstalleerd is. De patch-id is MDVA-35254. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.1-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

CAPTCHA configureren:

1. Een andere betalingsprovider installeren en configureren (bijvoorbeeld Braintree).
1. Ga naar **Opslag > Configuratie > Klant > de Configuratie van de Klant > CAPTCHA > Forms**.
1. Selecteer **Controle/Plaatsende Orde**.
1. Houd het **Aantal Onsuccesvolle Pogingen aan Login** als gebrek (gebrek = *3*).
1. Meld u aan als klant.
1. Voeg een product toe aan het winkelwagentje.
1. Ga naar het betalingsgedeelte bij de afhandeling.
1. Selecteer **de betaalmethode van de Kaart van de Krediet** (Voorbeeld: Braintree).
1. Voer drie mislukte betalingspogingen uit.

<u> Verwachte resultaten </u>:

Het veld CAPTCHA wordt weergegeven wanneer het aantal mislukte pogingen is bereikt.

<u> Ware resultaten </u>:

Het gebied CAPTCHA toont nooit, slechts het foutenbericht: *gelieve te verstrekken code CAPTCHA en opnieuw te proberen.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
