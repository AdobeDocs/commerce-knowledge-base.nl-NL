---
title: 'MDVA-32634 patch: move category in hiërarchie url_path wrong'
description: Met de MDVA-32634-patch wordt het probleem opgelost waarbij de URL\_path van de cataloguscategorie niet verandert nadat de categorie in de hiërarchie is verplaatst. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: a445dea6-3834-479b-9044-b6d2b863a0b5
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# MDVA-32634 patch: move category in hiërarchie url_path wrong

Met de MDVA-32634-patch wordt het probleem opgelost waarbij de URL\_path van de cataloguscategorie niet verandert nadat de categorie in de hiërarchie is verplaatst. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.1 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een cataloguscategorie in de hiërarchie verplaatst, resulteert dit in een onjuiste URL\_path. De URL\_path van de categorie die is toegewezen aan het standaardbereik van de winkel \[ **id:0** \] blijft ongewijzigd nadat de categorie in de hiërarchie is verplaatst.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de Commerce-beheerder. De volgende categoriestructuur maken onder de hoofdcategorie: move-cat sub-move-cat sub-move-cat2 new-cat-move
1. Verifieer categorie \[ url\_path \] kenmerk \[ id: 120 \] voor waardetoewijzing in \[ catalog\_category\_entity\_varchar \] tabel met de volgende query:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   Het zou u het volgende resultaat moeten geven:

   ```sql
   MariaDB [m24dev]> SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   \[ url\_path \] waarden zijn gegenereerd en toegewezen aan Al Store-bereik \[ 0 \]. Dit is juist in vergelijking met een instantie zonder B2B.
1. Ga naar de lijst met achterste categorieën, sleep \[ move-cat \] en zet deze neer in \[ new-cat-move \]. De categorie moet er nu als volgt uitzien: new-cat-move-cat sub-move-cat sub-cat2
1. Controleer de tabel \[ catalog\_category\_entity\_varchar \] met de volgende query:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 16;
   ```

<u>Verwachte resultaten</u>:

De URL\_path die is toegewezen aan al het opslagbereik \[ 0 \], moet ook worden bijgewerkt met het nieuwe pad.

<u>Werkelijke resultaten</u>:

De URL\_path die is toegewezen aan al het opslagbereik \[ 0 \], blijft ongewijzigd, ook al is dit pad niet beschikbaar na de verplaatsing. Bovendien worden voor elke winkel nieuwe waarden voor url\_path gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
