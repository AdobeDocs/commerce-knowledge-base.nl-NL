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

Dit artikel verstrekt een oplossing voor wanneer een plaatsing ontbreekt en u hebt de volgende fout in opstellen logboek: *huidige versie van RDBMS wordt niet gesteund*.

## Betrokken producten en versies

Adobe Commerce on cloud Infrastructure, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## Probleem

Dit foutbericht betekent dat de huidige versie van MariaDB niet meer wordt ondersteund in de Adobe Commerce-versie waarnaar u wilt upgraden en dat MariaDB moet worden bijgewerkt naar een compatibele versie.


<u> Stappen om </u> te reproduceren:

Poging om te implementeren.

<u> Verwacht resultaat </u>:

Succesvolle implementatie.

<u> Werkelijk resultaat </u>:

De plaatsing ontbreekt met foutenmelding: *huidige versie van RDBMS wordt niet gesteund*.

## Oorzaak

Uw versie van MariaDB is niet compatibel met de versie van Adobe Commerce waarnaar u probeert te upgraden.

## Oplossing

U moet de MariaDB-service upgraden naar een compatibele versie voordat u de toepassing upgradet.


Voor de integratietak op Adobe Commerce op de architectuur van het plan van de wolkeninfrastructuur Pro (en alle takken in de architectuur van de Aanzet) te volgen gelieve [ de Dienst ](https://devdocs.magento.com/cloud/project/services.html) in onze ontwikkelaarsdocumentatie te vormen.

Voor het Staging en de Productie op Adobe Commerce op de architectuur van het Pro plan van de wolkeninfrastructuur, gelieve [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor te leggen om te verzoeken dat de diensten worden bevorderd alvorens u de versie van Adobe Commerce opstelt.


## Gerelateerde lezing

* [ Beste praktijken voor bouwt en plaatsing ](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) in onze ontwikkelaarsdocumentatie.
* [ Adobe Commerce 2.3.5 verbetering: compact aan dynamische lijsten ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) in onze steun knowlegde basis.
