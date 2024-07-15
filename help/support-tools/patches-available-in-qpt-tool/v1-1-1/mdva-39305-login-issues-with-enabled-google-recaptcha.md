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

De MDVA-39305-patch verhelpt het probleem dat geregistreerde klanten zich niet kunnen aanmelden met de ingeschakelde Google reCAPTCHA. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 geïnstalleerd is. De patch-id is MDVA-39305. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.4 en 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce on cloud Infrastructure 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Geregistreerde klanten kunnen zich niet aanmelden met de ingeschakelde Google reCAPTCHA.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > **Configuratie** > **Veiligheid** > **Google reCAPTCHA Storefront** en laat **Google reCAPTCHA** toe.
1. Ga naar **Frontend**.
1. Open **Console van het Hulpmiddel van de Ontwikkelaar** in browser.

<u> Verwachte resultaten </u>:

Geen CSP waarschuwingen in de console.

<u> Ware resultaten </u>:

CSP waarschuwingen in de console.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
