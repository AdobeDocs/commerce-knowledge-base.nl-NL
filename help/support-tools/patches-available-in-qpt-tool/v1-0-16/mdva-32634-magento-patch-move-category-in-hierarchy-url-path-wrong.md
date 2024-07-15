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

Met de MDVA-32634-patch wordt het probleem opgelost waarbij de URL\_path van de cataloguscategorie niet verandert nadat de categorie in de hiërarchie is verplaatst. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.1 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een cataloguscategorie in de hiërarchie verplaatst, resulteert dit in een onjuiste URL\_path. De url \_path van de categorie die aan het standaardopslagwerkingsgebied \ [ **wordt toegewezen identiteitskaart:0** \] blijft onveranderd na het bewegen van de categorie in de hiërarchie.

<u> Stappen om </u> te reproduceren:

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

<u> Verwachte resultaten </u>:

De URL\_path die is toegewezen aan al het opslagbereik \[ 0 \], moet ook worden bijgewerkt met het nieuwe pad.

<u> Ware resultaten </u>:

De URL\_path die is toegewezen aan al het opslagbereik \[ 0 \], blijft ongewijzigd, ook al is dit pad niet beschikbaar na de verplaatsing. Bovendien worden voor elke winkel nieuwe waarden voor url\_path gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
