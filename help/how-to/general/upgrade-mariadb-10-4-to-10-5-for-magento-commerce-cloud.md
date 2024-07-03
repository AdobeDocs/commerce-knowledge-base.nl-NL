---
title: Upgrade MariaDB 10.4 naar 10.5 voor Adobe Commerce op cloud
description: MariaDB 10.4 eindigt op 18 juni 2024. In dit artikel wordt uitgelegd hoe u MariaDB kunt upgraden van 10,4 naar 10,5 en Adobe Commerce kunt blijven gebruiken voor cloudinfrastructuur.
feature: Best Practices, Cloud
exl-id: 065840b8-28c1-4686-95fc-df3e73152845
source-git-commit: 11f2fae3264a61413c5da1b93ef4980151a1df1e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Upgrade MariaDB 10.4 naar 10.5 voor Adobe Commerce op cloud

MariaDB is een open-sourcedatabase voor bedrijven die met Adobe Commerce wordt gebruikt.

MariaDB 10.4 bereikt het einde van de ondersteuning op [18 juni 2024](https://endoflife.date/mariadb). U bent niet meer PCI-compatibel wanneer u een niet-ondersteunde versie van MariaDB gebruikt. In dit artikel wordt uitgelegd hoe u van MariaDB 10.4 naar 10.5 kunt upgraden om Adobe Commerce te blijven gebruiken voor cloudinfrastructuur.

>[!NOTE]
>
>Aangezien MariaDB 10.4 einde-van-leven (EOL) bereikt, zal het niet meer in huidige versies van Adobe Commerce worden gesteund. Het is aan te raden om een EOL-versie binnen 30 dagen na de EOL uit te schakelen.

## Betrokken product en versies

* Alle Adobe Commerce op locatie en op cloudinfrastructuur 2.4.4 en 2.4.5

## Oplossing

Goedkeuren van de nieuwe beveiligingspatches (2.4.4-p9 of 2.4.5-p8) die op 11 juni 2024 worden uitgebracht, om te zorgen voor compatibiliteit met MariaDB 10.5. Voer vervolgens de onderstaande stappen uit om van MariaDB 10.4 naar 10.5 te upgraden.

### Upgradestappen voor cloudimplementaties

1. Een [DB-back-up met opdrachten voor databaseback-up met ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Deze reservekopie moet worden uitgevoerd vóór stap 2 en 3 als er iets verkeerd gaat tijdens het bijwerken van tabellen/rijen.
1. [Alle compacte tabellen controleren en converteren naar dynamische tabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade). Deze stap wordt vereist om potentieel gegevensverlies tijdens de gegevensbestandverbetering te vermijden.
1. Controleren op MYISAM-tabellen. U moet [Alle MyISAM-tabellen converteren naar InnoD](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud).
1. Nadat u de databasetabellen en -rijen hebt voorbereid (de vorige twee stappen), maakt u een [DB-back-up met opdrachten voor databaseback-up met ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Een ondersteuningsticket openen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om de upgrade van MariaDB 10.4 naar 10.5 te plannen. Geef in het ticket de datum en tijd op waarop u de DB-upgrade wilt uitvoeren. Het ondersteuningsteam heeft een opzegtermijn van 48 uur nodig en het ontwikkelingsteam van de handelaar moet beschikbaar zijn. Zodra de tijd en de datum voor de verbetering worden overeengekomen, doe het volgende:
   1. Zet uw plaats in onderhoudswijze, en stop om het even welke activiteiten van DB, bijvoorbeeld, bakens.
   1. Een [DB-back-up met opdrachten voor databaseback-up met ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Laat de support weten dat u de back-up hebt voltooid via uw ondersteuningsticket. Raadpleeg voor meer informatie over het bekijken en volgen van uw tickets [Adobe Commerce Help Center - Gebruikershandleiding: uw ticket bijhouden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in onze kennisbasis voor ondersteuning.
   1. Het Adobe Commerce-ondersteuningsteam start vervolgens het MariaDB-upgradeproces. Als alle bovenstaande stappen zijn uitgevoerd en de database een gemiddelde grootte heeft, duurt het proces ongeveer een uur. Grotere database&#39;s duren langer. Zodra de upgrade is voltooid, wordt u op de hoogte gesteld via uw ticket.
1. Onderhoudsmodus uitschakelen. Zie [Onderhoudsmodus in- of uitschakelen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in onze ontwikkelaarsdocumentatie.

>[!NOTE]
>
>U wordt aangeraden een DB-back-up te maken voor en na elke upgrade, zodat gegevensverlies niet meer mogelijk is. Hierdoor kunt u terugdraaien naar een vorige stap als er problemen optreden tijdens het upgraden van de versie.

## Verwante lezing

* [Handleiding voor aanbevolen procedures voor DB-upgrades](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites) voor plaatsingen ter plaatse.
* [Upgrade MariaDB 10.0 naar 10.2 voor Adobe Commerce op cloud](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud) in onze kennisbasis voor ondersteuning.
* [Adobe Commerce-levenscyclusbeleid](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) in onze ontwikkelaarsdocumentatie.
