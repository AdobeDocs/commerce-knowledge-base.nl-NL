---
title: 'MDVA-34847: customer_grid_flat table slow query'
description: De flard MDVA-34847 lost de kwestie op waar de langzame vragen op de lijst ` customer_grid_flat ` voorkomen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: e91cb86d-83cd-4267-a132-64465a57da7f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-34847: customer_grid_flat table slowaakse vragen

De patch MDVA-34847 lost het probleem op waar de langzame vragen op de `customer_grid_flat` lijst voorkomen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.3.3

**Compatibel met de versies van de Adobe:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Langzame query&#39;s vinden plaats in de `customer_grid_flat` -tabel.

<u> Stappen om </u> te reproduceren:

1. Creeer een gebruiker Admin met een werkingsgebied van de Douane (Voorbeeld: Plaats **GWS** = *0,* en kies de bestaande standaardwebsite met **identiteitskaart** = *1*).
1. Maak alle producten en rubrieken.
1. Plaats een volgorde vanaf de voorkant.
1. Meld u aan bij de beheerder als de nieuwe gebruiker.
1. Ga naar het net van de Verkoop (**Verkoop > Orden**).
1. Controleer of de SQL-query naar DB (database) is verzonden.

<u> Verwachte resultaten </u>:

De Admin GWS-extensie moet

```sql
int
```

waarden van

```sql
website_id
```

in SQL-condities, zoals verwacht, zoals:

```sql
main_table.website_id IN (1)
```

<u> Ware resultaten </u>:

De Admin GWS-extensie heeft een voorwaarde toegevoegd met

```sql
website_id
```

waarde als

```sql
string
```

, zoals:

```sql
main_table.website_id IN ('1')
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
