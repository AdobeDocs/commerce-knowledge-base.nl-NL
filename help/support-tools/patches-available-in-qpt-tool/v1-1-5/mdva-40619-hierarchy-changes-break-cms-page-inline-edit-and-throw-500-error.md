---
title: 'MDVA-40619: Hierarchy changes break CMS page inline edit and throw 500 error'
description: De patch MDVA-40619 lost het probleem op waarbij de wijzigingen in de CMS-paginahiërarchie inline bewerken van CMS-pagina afbreken en "500 error" genereren. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-40619. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: c003d845-1ba0-49c0-9f1a-a4b0ec00f30c
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40619: De hiërarchie verandert onderbreekt CMS pagina inline uitgeven en werpt 500 fout

De patch MDVA-40619 lost het probleem op waarbij de wijzigingen in de CMS-paginahiërarchie inline bewerken van CMS-pagina afbreken en &quot;500 error&quot; genereren. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-40619. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wijzigingen in de CMS-paginahiërarchie zorgen voor inline bewerking van CMS-pagina en genereren &quot;500 fout&quot;.

<u>Stappen om te reproduceren</u>:

1. Ga naar het deelvenster Beheer > **Inhoud** > **Hiërarchie**.
1. Selecteer Standaardwinkelweergave.
1. Schakel &quot;De hiërarchie van bovenliggende knooppunten gebruiken&quot; uit.
1. Selecteer de pagina handmatig en klik op **Opslaan**.
1. Ga vervolgens naar **Inhoud** > **Pagina&#39;s**.
1. Probeer een CMS-pagina uit het raster te bewerken.
1. Klikken **Opslaan**.

<u>Verwachte resultaten</u>:

Pagina is opgeslagen.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op:

*Een technisch probleem met de server heeft een fout veroorzaakt. Probeer opnieuw om door te gaan wat u aan het doen was. Probeer het later opnieuw als het probleem zich blijft voordoen.*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
