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

Met de MDVA-38666-patch wordt het probleem opgelost waarbij de beheerder de configureerbare productopties in het winkelwagentje van de klant niet kan wijzigen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-3866. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruiker kan de configureerbare productopties in de winkelwagentje van de klant niet wijzigen.

<u>Stappen om te reproduceren</u>:

1. Stel het bereik van de klantenaccount in op Globaal.
1. Maak twee websites met winkels.
1. Maak twee configureerbare producten en wijs deze toe aan elke website.
1. Maak een klantenaccount in de frontend en log in.
1. Voeg een product toe aan het winkelwagentje en voer een afrekening uit (dit wordt gedaan om de prijsaanduiding op elke website anders te maken).
1. Voeg een product aan de kar toe en laat het achter.
1. Schakel over naar de tweede website en voeg het product toe aan de winkelwagentje (dezelfde aanmelding moet werken omdat het bereik van de klantenaccount is ingesteld op Global).
1. Open de klant via de beheerder en ga naar het tabblad Kar.
1. Van de opslagplaats van drop-down en probeer om de configuratie te veranderen.

<u>Verwachte resultaten</u>:

De gebruiker krijgt een popup met configureerbare opties.

<u>Werkelijke resultaten</u>:

Er wordt geen pop-upformulier weergegeven. De gebruiker kan de configuratie niet wijzigen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
