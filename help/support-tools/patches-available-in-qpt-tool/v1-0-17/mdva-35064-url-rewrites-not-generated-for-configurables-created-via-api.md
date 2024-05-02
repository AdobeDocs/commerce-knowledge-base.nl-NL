---
title: 'MDVA-35064: URL herschrijft niet gegenereerd voor configureerbare functies die via API zijn gemaakt'
description: De patch MDVA-35064 verhelpt het probleem dat URL-herschrijvingen niet worden gegenereerd voor "All store views" voor producten die via API zijn gemaakt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 0898c5b3-d361-4bcb-af3a-7f76ac8a23e1
feature: REST, Categories, Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-35064: URL herschrijft niet gegenereerd voor configureerbare functies die via API zijn gemaakt

De patch MDVA-35064 verhelpt het probleem dat URL-herschrijvingen niet worden gegenereerd voor &quot;All store views&quot; voor producten die via API zijn gemaakt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.3-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer configureerbare producten via API worden gemaakt, wordt de URL niet opnieuw geschreven.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe website, sla deze op en sla de weergave op.
1. Maak een nieuwe categorie.
1. Maak een nieuw product en wijs dit toe aan de nieuwe categorie.
1. Wijs het product toe aan de hoofdwebsite en de nieuwe website.
1. Controleer de URL-tabel en controleer of deze vermeldingen bevat voor het product, de categorie/het product voor elke winkel op elke website.
1. Product verwijderen voor de tweede website.

<u>Verwachte resultaten</u>:

De URL-tabel bevat alleen vermeldingen voor product, categorie/product voor de winkels op de eerste website.

<u>Werkelijke resultaten</u>:

De URL-tabel bevat URL-herschriften voor alle winkels op alle websites.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
