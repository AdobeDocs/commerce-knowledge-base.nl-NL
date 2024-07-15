---
title: 'MDVA-38666: Admin user is unable to change configurable product options'
description: Met de MDVA-38666-patch wordt het probleem opgelost waarbij de beheerder de configureerbare productopties in het winkelwagentje van de klant niet kan wijzigen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-3866. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 72440e47-1deb-41da-a225-d4bc73029ad5
feature: Admin Workspace, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-38666: Admin-gebruiker kan configureerbare productopties niet wijzigen

Met de MDVA-38666-patch wordt het probleem opgelost waarbij de beheerder de configureerbare productopties in het winkelwagentje van de klant niet kan wijzigen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 geïnstalleerd is. De patch-id is MDVA-3866. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruiker kan de configureerbare productopties in de winkelwagentje van de klant niet wijzigen.

<u> Stappen om </u> te reproduceren:

1. Stel het bereik van de klantenaccount in op Globaal.
1. Maak twee websites met winkels.
1. Maak twee configureerbare producten en wijs deze toe aan elke website.
1. Maak een klantenaccount in de frontend en log in.
1. Voeg een product toe aan het winkelwagentje en voer een afrekening uit (dit wordt gedaan om de prijsaanduiding op elke website anders te maken).
1. Voeg een product aan de kar toe en laat het achter.
1. Schakel over naar de tweede website en voeg het product toe aan de winkelwagentje (dezelfde aanmelding moet werken omdat het bereik van de klantenaccount is ingesteld op Global).
1. Open de klant via de beheerder en ga naar het tabblad Kar.
1. Van de opslagplaats van drop-down en probeer om de configuratie te veranderen.

<u> Verwachte resultaten </u>:

De gebruiker krijgt een popup met configureerbare opties.

<u> Ware resultaten </u>:

Er wordt geen pop-upformulier weergegeven. De gebruiker kan de configuratie niet wijzigen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
