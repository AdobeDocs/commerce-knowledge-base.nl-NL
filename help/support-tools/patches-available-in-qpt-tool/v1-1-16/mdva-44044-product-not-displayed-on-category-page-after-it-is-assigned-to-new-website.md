---
title: "MDVA-44044: Product dat niet op een categoriepagina wordt weergegeven nadat het aan een nieuwe website is toegewezen"
description: Met de MDVA-44044-patch wordt het probleem opgelost waarbij een product niet op de categoriepagina wordt weergegeven nadat het aan een nieuwe website is toegewezen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 is geïnstalleerd. De patch-id is MDVA-44044. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: e3a179ed-243c-4200-a01a-796657bd31ab
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-44044: Product wordt niet op categoriepagina weergegeven nadat het aan een nieuwe website is toegewezen

Met de MDVA-44044-patch wordt het probleem opgelost waarbij een product niet op de categoriepagina wordt weergegeven nadat het aan een nieuwe website is toegewezen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 is geïnstalleerd. De patch-id is MDVA-44044. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het product wordt niet op de categoriepagina weergegeven nadat het aan een nieuwe website is toegewezen.

<u>Stappen om te reproduceren</u>:

1. Stel de indexeermodus in op plannen.
1. Maak een secundaire website, sla deze op en sla de weergave op.
1. Een secundaire opslagcode toevoegen in `index.php`:

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. Maak een nieuwe categorie.
1. Maak een nieuw product dat is toegewezen aan de nieuwe categorie. Let erop dat u het alleen toewijst aan de primaire website.
1. Voer de uitsnede uit.
1. Open de categorie vanuit de winkel.
1. Wijs het product toe aan de secundaire website.
1. Voer de uitsnede opnieuw uit.

<u>Verwachte resultaten</u>:

Het product wordt op de categoriepagina weergegeven na een geplande indexeerprogramma.

<u>Werkelijke resultaten</u>:

Het product wordt pas op de categoriepagina weergegeven als het volledig opnieuw is samengesteld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
