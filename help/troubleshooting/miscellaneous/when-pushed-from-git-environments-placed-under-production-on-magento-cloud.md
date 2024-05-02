---
title: Nieuwe omgevingen die onder productie worden geplaatst wanneer ze van Git worden geduwd
description: Dit artikel biedt een oplossing voor het probleem dat nieuwe omgevingen onder de productieomgeving van Adobe Commerce op cloudinfrastructuur worden geplaatst wanneer ze van het git-versiebeheersysteem worden geduwd.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Nieuwe omgevingen die onder productie worden geplaatst wanneer ze van Git worden geduwd

Dit artikel biedt een oplossing voor het probleem dat nieuwe omgevingen onder de productieomgeving van Adobe Commerce op cloudinfrastructuur worden geplaatst wanneer ze van het git-versiebeheersysteem worden geduwd.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Probleem

<u>Vereisten</u>:

Een lokale, gecontroleerde kloon van het project hebben.

<u>Stappen om te reproduceren</u>:

U moet een integratietak van de het opvoeren tak tot stand brengen:

1. Ga naar de staging tak door de volgende opdracht in de lokale shell uit te voeren: `git checkout staging`
1. Creeer een integratietak van de het opvoeren tak door het volgende bevel in lokale shell in werking te stellen: `git checkout -b <branch>`
1. Druk de vertakking naar de externe opslagplaats en stel een stroomopwaartse vertakking in door de volgende opdracht in de lokale shell uit te voeren: `git push --set-upstream origin <branch>`

<u>Verwachte resultaten</u>:

De nieuwe tak wordt gecreeerd onder de het opvoeren tak.

<u>Werkelijke resultaten</u>:

De nieuwe tak werd opgericht onder de productietak.

## Oorzaak

Dit is geen bug. Voor het plaatsen van een oudertak voor een andere tak, zou de handelaar magento-wolk CLI moeten gebruiken.

## Oplossing

Een bovenliggende vertakking kan alleen worden ingesteld nadat de handelaar een nieuwe vertakking heeft geduwd en geactiveerd. Zie [Adobe Commerce on cloud Infrastructure > Bitmap Integration](https://devdocs.magento.com/cloud/integrations/bitbucket-integration.html#create-a-new-cloud-branch) in onze ontwikkelaarsdocumentatie.

Als u een bovenliggend item voor de bestaande vertakking op de server wilt bijwerken, gebruikt u de `magento-cloud environment:info` in de magento-cloud CLI.

Voorbeeld van het gebruik:

`magento-cloud environment:info parent Staging`

Hierdoor wordt de bovenliggende vertakking ingesteld op &quot;Staging&quot; voor de momenteel uitgecheckte vertakking.

## Gerelateerde lezing

* [Adobe Commerce on cloud Infrastructure > magento-cloud CLI](https://devdocs.magento.com/cloud/reference/cli-ref-topic.html) in onze ontwikkelaarsdocumentatie.
