---
title: Afbeeldingen van producten worden niet weergegeven ondanks de rollen voor productafbeeldingen bewerken
description: Dit artikel biedt een oplossing voor het feit dat productafbeeldingen niet worden weergegeven op de winkelpagina, ondanks de afbeeldingsrollen die zijn ingesteld op de pagina Product Edit.
exl-id: 456baa5a-fa16-4bc1-9d6c-54106fae58ca
feature: Cache, Products, Roles/Permissions, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Afbeeldingen van producten worden niet weergegeven ondanks de rollen voor productafbeeldingen bewerken

Dit artikel biedt een oplossing voor het feit dat productafbeeldingen niet worden weergegeven op de winkelpagina, ondanks de afbeeldingsrollen die zijn ingesteld op de pagina Product Edit.

**Oorzaak:** in Adobe Commerce-gevallen met meerdere winkels kunnen sommige productafbeeldingen de `no_selection` waarden voor afbeeldingsrolkenmerken `image`, `small_image`, `thumbnail`, `swatch`. Dergelijke `no_selection` De waarden verschijnen wanneer de rol van het productbeeld op het globale, alle-opslagwerkingsgebied in plaats van het werkingsgebied van een bepaalde opslag wordt geplaatst (met andere woorden, op **Alle winkelweergaven** in plaats van een bepaalde **Winkelweergave**). Om te begrijpen als dat uw geval is, stel het SQL manuscript van in werking **Oorzaak** hieronder.

**Oplossing:** rijen verwijderen met de `no_selection` waarden voor dergelijke beelden gebruiken het SQL manuscript van de sectie van de Oplossing hieronder.

## Betrokken versies

* Adobe Commerce op locatie 2.X.X
* Adobe Commerce op cloudinfrastructuur 2.X.X

## Probleem

Afbeeldingen van producten worden mogelijk niet weergegeven op de winkelpagina, hoewel de afbeeldingsrollen (Basis, Klein, Miniatuur, Staal) juist zijn ingesteld op de productpagina van het beheerpaneel.

Wanneer u de productpagina controleert met **Winkelweergave** instellen op **Alle winkelweergaven** heeft het beeld de rollen die op de **Afbeeldingsdetails** scherm.

![all_store_views.png](assets/all_store_views.png)

![image_rollen.png](assets/image_roles.png)

Op de winkel wordt de afbeelding echter niet weergegeven; wanneer u de productpagina op het specifieke archiefniveau controleert (en de **Winkelweergave**), is de afbeelding aanwezig maar zijn de rollen niet ingesteld.

![image_rollen_not_set.png](assets/image_roles_not_set.png)

## Oorzaak

Op de multi-store Adobe Commerce-instanties (met meerdere winkels) kunnen sommige productafbeeldingen de `no_selection` waarden voor kenmerken `image`, `small_image`, `thumbnail`, `swatch` (Deze kenmerken komen overeen met afbeeldingsrollen). Dergelijke `no_selection` De waarden verschijnen wanneer de rol van het productbeeld op het globale, alle-opslagwerkingsgebied in plaats van het werkingsgebied van een bepaalde opslag wordt geplaatst (met andere woorden, op **Alle winkelweergaven** in plaats van een bepaalde **Winkelweergave**).

Technisch gezien: aan `store_id=0` (die de globale montages voor alle opslag op uw instantie van Adobe Commerce houdt), zouden de de beeldrollen van het product kunnen worden geplaatst: dit betekent dat de attributen `image`, `small_image`, `thumbnail`, `swatch` hebben geldige waarden (pad naar afbeeldingen). Tegelijkertijd wordt `store_id=1` (dit is een speciale opslagweergave), de waarden voor deze kenmerken zijn `no_selection`.

### Hoe te om te verifiëren dat uw probleem is

Deze SQL-query uitvoeren:

```sql
SELECT `cpev_s`.*, `cpev_0`.`value` AS `store_value` FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

Als de vraag een resultaat als hieronder terugkeert, behandelt u het probleem dat in dit artikel wordt gedocumenteerd:

```sql
+----------+--------------+----------+--------+--------------+----------------------------+
| value_id | attribute_id | store_id | row_id | value        | store_value                |
+----------+--------------+----------+--------+--------------+----------------------------+
|    67722 |           87 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67723 |           88 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67724 |           89 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67814 |           87 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6769 |           87 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67815 |           88 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6770 |           88 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67816 |           89 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6771 |           89 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
+----------+--------------+----------+--------+--------------+----------------------------+
9 rows in set (0.06 sec)
```

### Waarom gebeurt dit?

Als de Adobe Commerce-toepassing meer dan één winkel heeft, worden gegevens mogelijk niet gesynchroniseerd tussen een bepaalde winkel en de algemene opslaginstellingen.

Waarden op `store_id=1` hebben meer prioriteit dan de standaard (globale) opslag (`store_id=0`). Aldus kan de toepassing de globale beeldmontages negeren en de configuratie van het archiefwerkingsgebied gebruiken (`no_selection` voor afbeeldingsrolkenmerken) bij het weergeven van een afbeelding.

## Oplossing {#solution}

Kenmerken verwijderen met de opdracht `no_selection` waarden met dit SQL-script:

```
DELETE `cpev_s`.* FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

Nadat deze attributen worden verwijderd, worden de rollen voor bepaalde opslag geplaatst en de beelden getoond op de storefront.

## Aanvullende gegevens

U kunt de resultaten van de correctie niet meteen zien als de optie Volledige paginacache in uw Adobe Commerce-exemplaar is ingeschakeld.

Voor de wijzigingen die u wilt weergeven, vernieuwt u de paginacache met de optie **Cachebeheer** van het deelvenster Beheer.

## Meer informatie

### Winkels en bereik

[Winkels en winkelbereik](/docs/commerce-admin/stores-sales/site-store/stores.html) in onze gebruikershandleiding

### Afbeeldingen

[Productafbeeldingen uploaden](/docs/commerce-admin/catalog/products/digital-assets/product-image.html#upload-an-image) in onze gebruikershandleiding

### Cache

* [Cachebeheer](/docs/commerce-admin/systems/tools/cache-management.html) in onze systeemhandleiding voor gebruikersbeheer.
* [De cache beheren](/docs/commerce-operations/configuration-guide/cli/manage-cache.html) in onze documentatie voor ontwikkelaars