---
title: De increment ID van een DB-entiteit wijzigen (order, factuur, creditnota, enz.) in een bepaald archief
description: In dit artikel wordt besproken hoe u de increment-id voor een Adobe Commerce Database-entiteit (DB) (bestelling, factuur, creditmemo, enz.) kunt wijzigen op een bepaalde Adobe Commerce-winkel die de SQL-instructie 'ALTER TABLE' gebruikt.
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# De increment ID van een DB-entiteit wijzigen (order, factuur, creditnota, enz.) in een bepaald archief

In dit artikel wordt besproken hoe u de increment-id voor een Adobe Commerce Database-entiteit (DB) (bestelling, factuur, creditmemo, enz.) kunt wijzigen in een bepaalde Adobe Commerce-winkel die de `ALTER TABLE` SQL-instructie.

## Betrokken versies

* Adobe Commerce op locatie: 2.x.x
* Adobe Commerce op cloud-infrastructuur: 2.x.x
* MySQL: alle [ondersteunde versie](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html#database)

## Wanneer moet u de increment-id (gevallen) wijzigen

In de volgende gevallen moet u mogelijk de increment-id wijzigen voor nieuwe DB-entiteiten:

* Na een harde back-up herstellen op een live site
* Sommige transactiebestanden zijn verloren gegaan, maar hun id&#39;s worden al gebruikt door betalingsgateways (zoals PayPal) voor uw huidige Merchant-account. In dat geval verwerken de betaalgateways geen nieuwe orders met dezelfde id en wordt de fout &#39;&#39;Dubbele factuur-id&#39;&#39; geretourneerd

>[!NOTE]
>
>U kunt het probleem met de betaalgateway voor PayPal ook verhelpen door meerdere betalingen per factuur-ID toe te staan in de voorkeuren voor betalingsontvangst van PayPal. Zie [PayPal-gateway afgewezen aanvraag - dubbele factuurkwestie](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) in onze kennisbasis voor ondersteuning.

## Vereiste stappen

1. Zoek opslagruimten en entiteiten waarvoor de nieuwe verhogings-id moet worden gewijzigd.
1. [Verbinden](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) naar uw MySQL-database. Voor Adobe Commerce op cloudinfrastructuur moet u [SSH voor uw omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Controleer de huidige auto\_increment waarde voor de lijst van de entiteitopeenvolging gebruikend de volgende vraag:

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Voorbeeld

Als u een automatische verhoging voor een orde in de opslag controleert met *ID=1* De tabelnaam zou dan als volgt zijn:

```sql
'sequence_order_1'
```

Als de waarde van de `auto_increment` column is *1234*, de volgende volgorde die bij de winkel wordt geplaatst *ID=1* de *ID \#100001234*.

### Gerelateerde documentatie

* [Een externe MySQL-databaseverbinding instellen](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) in onze ontwikkelaarsdocumentatie.

## Entiteit bijwerken om increment-id te wijzigen

Werk de entiteit bij met behulp van de volgende query:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>Belangrijk: de nieuwe verhogingswaarde moet groter zijn dan de huidige, niet minder!

### Voorbeeld

Na het uitvoeren van de volgende query:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

de volgende volgorde die bij de winkel wordt geplaatst *ID=1* de *ID \#100002000*.

## Aanvullende aanbevolen stappen voor productieomgeving (Cloud)

Voordat u het dialoogvenster `ALTER TABLE` We raden u ten zeerste aan om de volgende stappen uit te voeren in de Productie-omgeving van Adobe Commerce op het gebied van cloudinfrastructuur:

* Test de volledige procedure om verhogingsidentiteitskaart op uw milieu van het Staging te veranderen
* [Maken](/help/how-to/general/create-database-dump-on-cloud.md) een DB-back-up om de productiedatabase te herstellen in geval van een storing

## Gerelateerde documentatie

* [Database-dump maken op Cloud](/help/how-to/general/create-database-dump-on-cloud.md) in onze kennisbasis voor ondersteuning.
* [SSH voor uw omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) in onze ontwikkelaarsdocumentatie.
