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

De MDVA-34847-patch lost het probleem op waarbij trage query&#39;s optreden op de `customer_grid_flat` tabel. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.3

**Compatibel met Adobe versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Langzame vragen komen voor op de `customer_grid_flat` tabel.

<u>Stappen om te reproduceren</u>:

1. Een Admin-gebruiker met een aangepast bereik maken (bijvoorbeeld Set **GWS** = *0,* en kies de bestaande standaardwebsite met **ID** = *1*).
1. Maak alle producten en rubrieken.
1. Plaats een volgorde vanaf de voorkant.
1. Meld u aan bij de beheerder als de nieuwe gebruiker.
1. Ga naar het verkoopraster (**Verkoop > Bestellingen**).
1. Controleer of de SQL-query naar DB (database) is verzonden.

<u>Verwachte resultaten</u>:

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

<u>Werkelijke resultaten</u>:

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

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
