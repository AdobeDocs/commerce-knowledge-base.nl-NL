---
title: 'MDVA-42689: Gebruikers krijgen een fout wegens schending van integriteitsbeperking tijdens het bijwerken van productcategorieën tijdens het importeren'
description: De MDVA-42689-patch lost het probleem op waarbij gebruikers een fout wegens schending van integriteitsbeperking krijgen tijdens het bijwerken van productcategorieën tijdens het importeren. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-42689. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 7beff3bb-9313-43dc-be96-e33eff52a38e
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-42689: Gebruikers krijgen een fout wegens schending van integriteitsbeperking tijdens het bijwerken van productcategorieën tijdens het importeren

De MDVA-42689-patch lost het probleem op waarbij gebruikers een fout wegens schending van integriteitsbeperking krijgen tijdens het bijwerken van productcategorieën tijdens het importeren. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-42689. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Adobe Commerce genereert een fout met betrekking tot schending van integriteitsbeperking tijdens het bijwerken van productcategorieën tijdens het importeren.

<u>Stappen om te reproduceren</u>:

1. Stel twee websites in.
1. Maak subcategorieën onder de hoofdcategorie tot twee niveaus op de categoriepagina. Bijvoorbeeld hoofdcategorie > **Tandwiel** > **Controles**.
1. Twee eenvoudige producten maken en beide producten aan hetzelfde product toewijzen **Tandwiel** > **Controles** categorie.
1. Wijs één eenvoudig product aan beide websites toe.
1. Sla het product op.
1. Een CSV-bestand voorbereiden voor importeren. Er moeten twee productrecords met verschillende winkelweergaven zijn. Een van de producten moet bij beide winkelweergaven horen.
1. Importeer nu het CSV-bestand door naar **Systeem** > **Importeren** > **Type entiteit** (Producten).

<u>Verwachte resultaten</u>:

CSV-bestand wordt zonder fout geïmporteerd.

<u>Werkelijke resultaten</u>:

Adobe Commerce genereert de volgende fout:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
