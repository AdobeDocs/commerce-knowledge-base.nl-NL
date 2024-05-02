---
title: 'MDVA-44940: SQL-fout bij het opslaan van een categorie van beheerder'
description: De MDVA-44940-patch verhelpt het probleem waarbij een SQL-fout optreedt tijdens het opslaan van een categorie via de beheerder. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 is geïnstalleerd. De patch-id is MDVA-44940. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: cae6f231-3b91-441f-af56-824db0fa2d32
feature: Admin Workspace, Categories, Sales Channels
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-44940: SQL-fout bij het opslaan van een categorie van beheerder

De MDVA-44940-patch verhelpt het probleem waarbij een SQL-fout optreedt tijdens het opslaan van een categorie via de beheerder. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 is geïnstalleerd. De patch-id is MDVA-44940. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een SQL-fout op wanneer u een categorie opslaat via de beheerder.

<u>Stappen om te reproduceren</u>:

1. Voorbeeldgegevens installeren.
1. Maak een tweede website waaraan een opslaggroep is toegewezen aan de standaardcategorie.

   * Creeer een opslagmening die aan de nieuwe archiefgroep wordt toegewezen.

1. Maak voorraad en een extra bron die aan deze voorraad is toegewezen en een verkoopkanaal die aan de tweede website is toegewezen.
1. Maak een testproduct dat is toegewezen aan de tweede website.
1. Ga naar **Beheerder** > **Catalogus** > **Categorieën**, selecteert u **Toepassingsgebied** = **Tweede website** en ga naar **Producten in categorie** > **Automatisch sorteren** > Producten uit voorraad naar beneden verplaatsen en klikken **Opslaan**.

<u>Verwachte resultaten</u>:

De categorie wordt opgeslagen.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op: *Er is iets misgegaan tijdens het opslaan van de categorie*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
