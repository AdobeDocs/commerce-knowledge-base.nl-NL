---
title: Grote MySQL-tabellen zoeken
description: '"Om de grote lijsten te identificeren, verbind met het gegevensbestand zoals die in het [verbindt met het gegevensbestand] (https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) artikel wordt beschreven, en stel het volgende bevel in werking, waar ` project_id'' uw het project ID van de Wolk is:'''
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Grote MySQL-tabellen zoeken

Om de grote lijsten te identificeren, verbind met het gegevensbestand zoals die in wordt beschreven [Verbinding maken met de database](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) artikel en voer de volgende opdracht uit, waarbij `project_id` is uw Cloud-project-id:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Dit zou de volledige lijst van lijsten en hun grootte tonen. U kunt door de lijst gaan en identificeren welke lijsten aandacht wegens de grote grootte vereisen.
