---
title: 'MDVA-43601: Triggers worden verwijderd uit de tabel "catalogrule_product_price" na volledige herindex'
description: De flard MDVA-43601 lost de kwestie op waar de trekkers uit lijst ` catalogrule_product_price ` na een volledige herindex van catalogrule_rule of ` catalogrule_product ` worden verwijderd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43601. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601: Triggers worden verwijderd uit de tabel &quot;catalogrule_product_price&quot; na volledige herindex

De patch MDVA-43601 verhelpt het probleem waarbij triggers uit `catalogrule_product_price` -tabel worden verwijderd na een volledige redex van `catalogrule_rule` of `catalogrule_product` . Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 geïnstalleerd is. De patch-id is MDVA-43601. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Triggers worden verwijderd uit de tabel `catalogrule_product_price` nadat `catalogrule_rule` of `catalogrule_product` volledig opnieuw is gecomprimeerd.

<u> Stappen om </u> te reproduceren:

1. Plaats alle indexen aan *Update door Programma*.
1. Controleer de triggers die voor de tabel `catalogrule_product_price` zijn gemaakt door de volgende SQL-aanvraag uit te voeren:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Handmatig opnieuw indexeren `catalogrule_rule` of `catalogrule_product` door de volgende opdracht uit te voeren: `bin/magento indexer:reindex catalogrule_rule`
1. Controleer opnieuw de triggers van `catalogrule_product_price` table.

<u> Verwachte resultaten </u>:

Triggers in `catalogrule_product_price` -tabel blijven behouden na een volledige redex.

<u> Ware resultaten </u>:

Er zijn geen triggers gevonden voor de tabel `catalogrule_product_price` .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
