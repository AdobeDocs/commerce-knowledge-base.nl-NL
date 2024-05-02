---
title: Overschakelen naar OpenSearch for Adobe Commerce op Cloud 2.4.4
promoted: true
description: Adobe Commerce on cloud Infrastructure 2.4.4 ondersteunt geen versies van Elasticsearch na 7.10. **U moet eerst upgraden naar Adobe Commerce 2.4.4 en vervolgens meteen overschakelen van Elasticsearch naar OpenSearch 1.2.x.** Adobe zal gedetailleerde instructies geven die dichter bij de Adobe Commerce 2.4.4 GA-release liggen.
exl-id: 0cb34cee-d4d9-428e-a7fd-7301a86dd8f6
feature: Cloud, Iaas, Paas, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Overschakelen naar OpenSearch for Adobe Commerce op Cloud 2.4.4

Adobe Commerce on cloud Infrastructure 2.4.4 ondersteunt geen versies van Elasticsearch na 7.10. **U moet eerst upgraden naar Adobe Commerce 2.4.4 en dan meteen overschakelen van Elasticsearch naar OpenSearch 1.2.x.** Adobe zal gedetailleerde instructies geven die dichter bij de Adobe Commerce 2.4.4 GA-release liggen.

>[!NOTE]
>
>De schakelaar zou ongeacht wolkenleverancier moeten worden gedaan.

Adobe Commerce op locatie voegt ondersteuning toe voor Elasticsearch 7.16 en OpenSearch 1.2 in alle patchreleases van maart 2022 (2.4.4, 2.4.3-p2 en 2.3.7-p3). In 2.4.4 wordt Adobe Commerce op cloudinfrastructuur overgeschakeld naar OpenSearch als standaard zoekmachine. Handelaars moeten daarom OpenSearch gebruiken in plaats van Elasticsearch voordat ze een upgrade naar Adobe Commerce 2.4.4 of hoger uitvoeren. Handelaars met Adobe Commerce on-premisse plaatsingen kunnen Elasticsearch of OpenSearch gebruiken omdat Adobe Commerce beide zal blijven steunen.


## Wat is OpenSearch?

OpenSearch is een vork in Elasticsearch en Kibana. Het wordt onderhouden door AWS in plaats van Elastic.co. Om meer te leren, herzie GitHub [openssearch-project/OpenSearch](https://github.com/opensearch-project/OpenSearch).

**Compatibiliteit tussen versies:**

**Zal Adobe Commerce op cloud-infrastructuren Elasticsearch 7.10 ondersteunen?**

**Ja** - vanaf medio januari 2022 biedt Adobe Commerce ondersteuning voor cloudinfrastructuurversies 2.4.3-p1, 2.4.3-p2 en 2.3.7-p3 Elasticsearch 7.10.

Voor Adobe Commerce op locatie wordt de nieuwste versie 7.16.x aanbevolen om Log4j te beperken.

## Migratie:

## Wanneer kunnen handelaren migreren naar OpenSearch?

Na Adobe Commerce 2.4.4.

Voordat het upgradeproces naar Adobe Commerce 2.4.4 wordt gestart, moeten handelaren echter op een huidige versie van Adobe Commerce staan die Elasticsearch 7.10 ondersteunt en op zijn minst Elasticsearch hebben voordat het upgradeproces naar Adobe Commerce 2.4.4 of naar OpenSearch wordt gestart.

## Wat kunnen handelaren (Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie) die zich niet op 2.4.4 bevinden, doen? Kunnen ze upgraden naar een ondersteunde versie van Elasticsearch (7.10, 7.16.1) of naar OpenSearch? Moeten ze de nieuwste ondersteunde versie hebben (zoals 2.4.3-p1, 2.3.7-p2, 2.4.3-p1)?

Als de kernversie van Adobe Commerce deze versie ondersteunt, kan Elasticsearch 7.10 worden gebruikt.

Controleren [Systeemvereisten](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) in onze ontwikkelaarsdocumentatie voor versiecompatibiliteit.

>[!NOTE]
>
>Het wordt aanbevolen zo spoedig mogelijk een upgrade naar Adobe Commerce 2.4.4 uit te voeren, omdat Elasticsearch 7.10 in mei 2022 EOL zal zijn.

Adobe-partners kunnen zich aanmelden voor ons bètaprogramma [hier](https://experienceleague.adobe.com/docs/commerce-operations/release/beta-program.html) om toegang te krijgen tot onze nieuwste bètacode die is getest op Elasticsearch 7.16.1 en OpenSearch 1.1.
