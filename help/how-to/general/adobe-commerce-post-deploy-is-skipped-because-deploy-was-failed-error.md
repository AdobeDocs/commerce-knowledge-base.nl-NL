---
title: Adobe Commerce *post-implementatie wordt overgeslagen omdat implementatie is mislukt* fout
description: '''Dit artikel legt uit hoe te om een plaatsingsfout te onderzoeken: *Post-opstellen wordt overgeslagen omdat de implementatie ontbroken* was'
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Adobe Commerce *ná implementatie wordt overgeslagen omdat implementatie is mislukt* fout

Dit artikel verklaart hoe te om een plaatsingsfout te onderzoeken: *Post-implementatie wordt overgeslagen omdat de implementatie is mislukt* die optreedt tijdens de implementatie naar verschillende omgevingen, bijvoorbeeld de upgrade.

## Betrokken producten en versies

Adobe Commerce over cloudinfrastructuur [alle ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Probleem

De plaatsing ontbreekt en keert een generisch foutenbericht terug, zodat is het niet duidelijk op hoe te om de fout op te lossen.

## Oorzaak

Onbepaald - wat dit foutenbericht veroorzaakt hangt van de code en het gegevensbestand af dat wordt opgesteld.

## Hoe te om de plaatsingsfout te onderzoeken

```
[20XX-XX-XX XX:XX:XX] DEBUG: Running step: is-deploy-failed
    W:
    W: In Processor.php line 129:
    W:
    [20XX-XX-XX XX:XX:XX] ERROR: [201] Post-deploy is skipped because deploy was failed.
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: In DeployFailed.php line 39:
    W:
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: post-deploy
    W:
```

Om het foutenspoor te verkrijgen om de daadwerkelijke oorzaak te bepalen, SSH aan de server en het logboekdossier te controleren `var/log/install_upgrade.log`.
