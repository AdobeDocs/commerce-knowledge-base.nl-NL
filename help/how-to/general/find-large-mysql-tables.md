---
title: Grote MySQL-tabellen zoeken
description: 'Om de grote lijsten te identificeren, verbind met het gegevensbestand zoals die in [verbindt met het gegevensbestand] (https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) artikel wordt beschreven, en stel het volgende bevel in werking, waar project_id uw het projectidentiteitskaart van de Wolk is:'
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Grote MySQL-tabellen zoeken

Om de grote lijsten te identificeren, verbind met het gegevensbestand zoals die in [&#x200B; wordt beschreven verbind met het gegevensbestand &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) artikel, en stel het volgende bevel in werking, waar `project_id` uw het projectidentiteitskaart van de Wolk is:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Dit zou de volledige lijst van lijsten en hun grootte tonen. U kunt door de lijst gaan en identificeren welke lijsten aandacht wegens de grote grootte vereisen.

## Gerelateerde lezing

[&#x200B; Beste praktijken voor het wijzigen van gegevensbestandlijsten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
