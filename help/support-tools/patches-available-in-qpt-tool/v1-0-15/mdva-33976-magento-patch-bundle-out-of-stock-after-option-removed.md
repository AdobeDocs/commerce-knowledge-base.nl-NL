---
title: "MDVA-33976 patch: bundle Out of Stock after option removed"
description: De MDVA-33976-patch verhelpt de kwestie waarbij een bundelproduct als "Out of Stock" wordt weergegeven nadat een van de opties in Admin is verwijderd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: 2e2bc05b-ad31-4e87-b33e-3526f6a42478
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-33976 patch: bundle Out Of Stock after option removed

De MDVA-33976-patch verhelpt de kwestie waarbij een bundelproduct als &quot;Out of Stock&quot; wordt weergegeven nadat een van de opties in Admin is verwijderd. Deze pleister is beschikbaar wanneer de [Gereedschap Kwaliteitspatches (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.3.3

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0-2.3.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Open een bundelproduct in Commerce Admin.
1. Verwijder een van de opties voor het bundelproduct.
1. Wijzigingen opslaan.
1. Open het product op de winkel.

<u>Verwacht resultaat</u>:

De voorraadstatus van het bundelproduct wordt bijgewerkt volgens de status van de voorraad van het onderliggende product.

<u>Werkelijk resultaat</u>:

Het bundelproduct wordt weergegeven als Buiten-de-voorraad, ongeacht de status van het onderliggende product.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
