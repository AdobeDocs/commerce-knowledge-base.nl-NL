---
title: Upgrade MariaDB 10.0 naar 10.2 voor Adobe Commerce op cloud
description: MariaDB 10.0 en 10.1 zijn end-of-life (EOL). [De steun eindigde respectievelijk 31 maart 2019 en 17 oktober 2020](https://endoflife.date/mariadb). In dit artikel wordt uitgelegd hoe u MariaDB kunt upgraden van 10.0 naar 10.2 of 10.2 naar 10.3 of naar 10.4, om Adobe Commerce te gebruiken voor cloudinfrastructuur.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Upgrade MariaDB 10.0 naar 10.2 voor Adobe Commerce op cloud

MariaDB 10.0 en 10.1 zijn end-of-life (EOL). [De steun liep af op respectievelijk 31 maart 2019 en 17 okt 2020](https://endoflife.date/mariadb). In dit artikel wordt uitgelegd hoe u MariaDB kunt upgraden van 10.0 naar 10.2 of 10.2 naar 10.3 of naar 10.4, om Adobe Commerce te gebruiken voor cloudinfrastructuur.

>[!NOTE]
>
>MariaDB 10.0 is end-of-life (EOL) en wordt niet ondersteund in de huidige Adobe Commerce-versies. Het is aan te raden om een EOL-versie binnen 30 dagen na de EOL uit te schakelen.

## Betrokken product en versies

* MariaDB 10.2 wordt aanbevolen voor Adobe Commerce op cloudinfrastructuur 2.3.x.
* MariaDB 10.4 wordt aanbevolen voor 2.4.x. MariaDB 10.3 is ook compatibel met Adobe Commerce op wolkeninfrastructuur 2.4.x.

## Upgradestappen

Voer de volgende stappen uit om een upgrade uit te voeren van MariaDB 10.0 naar 10.2 of 10.2 naar 10.3 of naar 10.4:

1. Een [DB-back-up met opdrachten voor databaseback-up met ECE-Tools](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump). Dit moet vóór stap 2 en 3 gebeuren als er iets verkeerd gaat tijdens het bijwerken van tabellen/rijen.
1. [Alle compacte tabellen controleren en converteren naar dynamische tabellen](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html). Dit is nodig om mogelijk gegevensverlies tijdens de upgrade van de database te voorkomen.
1. Controleren op MYISAM-tabellen. U moet [Alle MyISAM-tabellen converteren naar InnoD](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
1. Nadat u de databasetabellen en -rijen hebt voorbereid (de vorige twee stappen), maakt u een [DB-back-up met opdrachten voor databaseback-up met ECE-Tools](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump).
1. [Een ondersteuningsticket openen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om de upgrade van MariaDB 10.0 naar 10.2 of 10.2 naar 10.3 of 10.4 te plannen. In het kaartendetail de datum en de tijd wanneer u DB wilt bevorderen. Het ondersteuningsteam heeft een opzegtermijn van 48 uur nodig en het team van verkopers moet beschikbaar zijn. Zodra de tijd en de datum voor de verbetering worden overeengekomen, doe het volgende:
   1. Zet uw site in de onderhoudsmodus en stop alle DB-activiteiten, bijvoorbeeld de crons.
   1. Een [DB-back-up met opdrachten voor databaseback-up met ECE-Tools](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump).
   1. Laat de ondersteuning weten dat u de back-up hebt voltooid. Doe dit via je steunticket. Raadpleeg voor meer informatie over het bekijken en volgen van uw tickets [Adobe Commerce Help Center - Gebruikershandleiding: uw ticket bijhouden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in onze kennisbasis voor ondersteuning.
   1. Het Adobe Commerce-ondersteuningsteam zal beginnen met het MariaDB-upgradeproces. Als alle bovenstaande stappen zijn uitgevoerd en de database een gemiddelde grootte heeft, kan dit over ongeveer een uur gebeuren. Grotere database&#39;s duren langer. U wordt via uw ticket op de hoogte gesteld zodra de upgrade is voltooid.
1. Onderhoudsmodus uitschakelen. Zie [Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html#instgde-cli-maint) in onze ontwikkelaarsdocumentatie.

## Verwante lezing

Raadpleeg voor meer informatie over Adobe Commerce 2.4.x de vereisten voor [Adobe Commerce 2.4-systeemvereisten > Database](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html#database) in onze ontwikkelaarsdocumentatie.
