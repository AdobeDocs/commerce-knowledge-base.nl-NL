---
title: De incrementele id wijzigen voor een DB-entiteit (bestelling, factuur, creditnota, enz.) in een bepaalde winkel
description: In dit artikel wordt beschreven hoe u de increment-id voor een Adobe Commerce-database-entiteit (order, factuur, creditnota, enz.) wijzigt in een bepaalde Adobe Commerce-winkel met behulp van de SQL-instructie 'ALTER TABLE'.
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: e33d0bf6c857d0d54ec1373db79910d78296b054
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# De incrementele id wijzigen voor een DB-entiteit (bestelling, factuur, creditnota, enz.) in een bepaalde winkel

In dit artikel wordt besproken hoe u de verhogings-id voor een Adobe Commerce-database-entiteit (volgorde, factuur, creditnota, enz.) in een bepaalde Adobe Commerce-winkel kunt wijzigen met de SQL-instructie `ALTER TABLE` .

>[!NOTE]
>
>In dit artikel wordt alleen beschreven hoe u de beginnumerieke waarde van de increment-id voor bestellingen, facturen, creditnota&#39;s enzovoort wijzigt.
>
>De code heeft geen betrekking op het wijzigen van de opmaak van de increment-id of het toevoegen van aangepaste voorvoegsels/achtervoegsels (bijvoorbeeld het wijzigen van 10000001 in ORDER-1000001, MYSTORE-1000001, 2A10000) 1, enz.)
>
>Als u de indeling wilt aanpassen, hebt u een aangepaste extensie of ontwikkelbewerking nodig.

## Betrokken versies

* Adobe Commerce op locatie: 2.x.x
* Adobe Commerce op cloud-infrastructuur: 2.x.x
* MySQL: om het even welke [&#x200B; gesteunde versie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/system-requirements)

## Wanneer moet u de increment-id (gevallen) wijzigen

In de volgende gevallen moet u mogelijk de increment-id wijzigen voor nieuwe DB-entiteiten:

* Na een harde back-up herstellen op een live site
* Sommige transactiebestanden zijn verloren gegaan, maar hun id&#39;s worden al gebruikt door betalingsgateways (zoals PayPal) voor uw huidige Merchant-account. In dat geval verwerken de betaalgateways geen nieuwe orders met dezelfde id en wordt de fout &#39;&#39;Dubbele factuur-id&#39;&#39; geretourneerd

>[!NOTE]
>
>U kunt het probleem met de betaalgateway voor PayPal ook verhelpen door meerdere betalingen per factuur-ID toe te staan in de voorkeuren voor betalingsontvangst van PayPal. Zie [&#x200B; PayPal gateway verworpen verzoek - dubbele factuurkwestie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26838) in onze basis van de steunkennis.

## Vereiste stappen

1. Zoek opslagruimten en entiteiten waarvoor de nieuwe verhogings-id moet worden gewijzigd.
1. [&#x200B; verbind &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote) met uw OB MySQL. Voor Adobe Commerce op wolkeninfrastructuur, eerst, moet u [&#x200B; SSH aan uw milieu &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=nl-NL).
1. Controleer de huidige auto\_increment waarde voor de lijst van de entiteitopeenvolging gebruikend de volgende vraag:

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Voorbeeld

Als u een auto-verhoging voor een orde op de opslag met *ID=1* controleert, zou de lijstnaam zijn:

```sql
'sequence_order_1'
```

Als de waarde van de `auto_increment` kolom *1234* is, zal de volgende orde die bij de opslag met *wordt geplaatst ID=1* *identiteitskaart \#100001234* hebben.

### Gerelateerde documentatie

* [&#x200B; Opstelling een verre MySQL gegevensbestandverbinding &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote) in onze ontwikkelaarsdocumentatie.

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

de volgende orde die bij de opslag met *wordt geplaatst ID=1* zal *identiteitskaart \#100002000* hebben.

## Aanvullende aanbevolen stappen voor productieomgeving (Cloud)

Voordat we de `ALTER TABLE` -query op de Production-omgeving van Adobe Commerce op cloudinfrastructuur uitvoeren, raden we u ten zeerste aan deze stappen uit te voeren:

* Test de volledige procedure om verhogingsidentiteitskaart op uw milieu van het Staging te veranderen
* [&#x200B; creeer &#x200B;](/help/how-to/general/create-database-dump-on-cloud.md) een steun van DB om uw productieOB in het geval van mislukking te herstellen

## Gerelateerde documentatie

* [&#x200B; creeer gegevensbestandstortplaats op Wolk &#x200B;](/help/how-to/general/create-database-dump-on-cloud.md) in onze basis van de steunkennis
* [&#x200B; SSH aan uw milieu &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=nl-NL) in onze ontwikkelingsdocumentatie
* [&#x200B; Beste praktijken voor het wijzigen van gegevensbestandlijsten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
