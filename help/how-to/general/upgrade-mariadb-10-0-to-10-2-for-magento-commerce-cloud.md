---
title: Upgrade MariaDB 10.0 naar 10.2 voor Adobe Commerce op cloud
description: MariaDB 10.0 en 10.1 zijn end-of-life (EOL). [De steun eindigde respectievelijk 31 maart 2019 en 17 oktober 2020](https://endoflife.date/mariadb). In dit artikel wordt uitgelegd hoe u MariaDB kunt upgraden van 10.0 naar 10.2 of 10.2 naar 10.3 of naar 10.4, om Adobe Commerce te gebruiken voor cloudinfrastructuur.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# Upgrade MariaDB 10.0 naar 10.2 voor Adobe Commerce op cloud

MariaDB 10.0 en 10.1 zijn end-of-life (EOL). [&#x200B; steun beëindigde 31 Mar 2019 en 17 okt 2020 respectievelijk &#x200B;](https://endoflife.date/mariadb). In dit artikel wordt uitgelegd hoe u MariaDB kunt upgraden van 10.0 naar 10.2 of 10.2 naar 10.3 of naar 10.4, om Adobe Commerce te gebruiken voor cloudinfrastructuur.

>[!NOTE]
>
>MariaDB 10.0 is end-of-life (EOL) en wordt niet ondersteund in de huidige Adobe Commerce-versies. Het is aan te raden om een EOL-versie binnen 30 dagen na de EOL uit te schakelen.

## Betrokken product en versies

* MariaDB 10.2 wordt aanbevolen voor Adobe Commerce op cloudinfrastructuur 2.3.x.
* MariaDB 10.4 wordt aanbevolen voor 2.4.x. MariaDB 10.3 is ook compatibel met Adobe Commerce op wolkeninfrastructuur 2.4.x.

## Upgradestappen

Voer de volgende stappen uit om een upgrade uit te voeren van MariaDB 10.0 naar 10.2 of 10.2 naar 10.3 of naar 10.4:

1. Creeer de steun van a [&#x200B; DB gebruikend ECE-Hulpmiddelen DB reservebevelen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Dit moet vóór stap 2 en 3 gebeuren als er iets verkeerd gaat tijdens het bijwerken van tabellen/rijen.
1. [&#x200B; Controle en zet alle compacte lijsten in dynamische lijsten &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html?lang=nl-NL) om. Dit is nodig om mogelijk gegevensverlies tijdens de upgrade van de database te voorkomen.
1. Controleren op MYISAM-tabellen. U moet [&#x200B; alle lijsten MyISAM in InnoD &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=nl-NL) omzetten.
1. Nadat u de gegevensbestandlijsten en rijen (de vorige twee stappen) hebt voorbereid, creeer de steun van a [- OB gebruikend de reserve van ECE-Hulpmiddelen OB &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [&#x200B; Open een steunkaartje &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) om de verbetering van MariaDB 10.0 aan 10.2 of 10.2 aan 10.3 of 10.4 te plannen. In het kaartendetail de datum en de tijd wanneer u DB wilt bevorderen. Het ondersteuningsteam heeft een opzegtermijn van 48 uur nodig en het team van verkopers moet beschikbaar zijn. Zodra de tijd en de datum voor de verbetering worden overeengekomen, doe het volgende:
   1. Zet uw site in de onderhoudsmodus en stop alle DB-activiteiten, bijvoorbeeld de crons.
   1. Creeer de steun van a [&#x200B; DB gebruikend ECE-Hulpmiddelen DB reservebevelen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Laat de ondersteuning weten dat u de back-up hebt voltooid. Doe dit via je steunticket. Om stappen voor het bekijken van en het volgen van uw kaartjes te krijgen, verwijs naar [&#x200B; Gids van de Gebruiker van het Centrum van de Hulp van Adobe Commerce: Spoor uw Tickets &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#track-tickets) in onze basis van steunkennis.
   1. Het Adobe Commerce-ondersteuningsteam zal beginnen met het MariaDB-upgradeproces. Als alle bovenstaande stappen zijn uitgevoerd en de database een gemiddelde grootte heeft, kan dit over ongeveer een uur gebeuren. Grotere database&#39;s duren langer. U wordt via uw ticket op de hoogte gesteld zodra de upgrade is voltooid.
1. Onderhoudsmodus uitschakelen. Verwijs naar [&#x200B; toe of onbruikbaar maken onderhoudswijze &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in onze ontwikkelaarsdocumentatie.

## Verwante lezing

Meer over vereisten voor Adobe Commerce 2.4.x leren, verwijs naar [&#x200B; Adobe Commerce 2.4 systeemvereisten > Gegevensbestand &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/system-requirements#database) in onze ontwikkelaarsdocumentatie.
