---
title: De fout 'Huidige versie van RDBMS wordt niet ondersteund' bij de implementatie
description: 'Dit artikel biedt een oplossing voor het geval een implementatie mislukt en u hebt de volgende fout in het implementatielogboek: *current versie van RDBMS wordt niet ondersteund*.'
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# De fout &#39;Huidige versie van RDBMS wordt niet ondersteund&#39; bij de implementatie

Dit artikel verstrekt een oplossing voor wanneer een plaatsing ontbreekt en u hebt de volgende fout in opstellen logboek: *huidige versie van RDBMS wordt niet ondersteund*.

## Betrokken producten en versies

Adobe Commerce on cloud Infrastructure, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## Probleem

Dit foutbericht betekent dat de huidige versie van MariaDB niet meer wordt ondersteund in de Adobe Commerce-versie waarnaar u wilt upgraden en dat MariaDB moet worden bijgewerkt naar een compatibele versie.


<u>Stappen om te reproduceren</u>:

Poging om te implementeren.

<u>Verwacht resultaat</u>:

Succesvolle implementatie.

<u>Werkelijk resultaat</u>:

Implementatie mislukt met foutbericht: *huidige versie van RDBMS wordt niet ondersteund*.

## Oorzaak

Uw versie van MariaDB is niet compatibel met de versie van Adobe Commerce waarnaar u probeert te upgraden.

## Oplossing

U moet de MariaDB-service upgraden naar een compatibele versie voordat u de toepassing upgradet.


Voor de integratie-tak op Adobe Commerce op de architectuur van het Pro-abonnement voor cloudinfrastructuur (en alle takken in de Starter-architectuur) volgt u [Service configureren](https://devdocs.magento.com/cloud/project/services.html) in onze ontwikkelaarsdocumentatie.

Voor de Staging and Production op Adobe Commerce over cloudinfrastructuur Pro kunt u [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om aan te vragen dat de services worden bijgewerkt voordat u de Adobe Commerce-versie-upgrade implementeert.


## Gerelateerde lezing

* [Aanbevolen werkwijzen voor builds en implementatie](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) in onze ontwikkelaarsdocumentatie.
* [Adobe Commerce 2.3.5-upgrade: compact naar dynamische tabellen](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) in onze steun knowlegde basis.
