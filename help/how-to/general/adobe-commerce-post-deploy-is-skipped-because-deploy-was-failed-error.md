---
title: Adobe Commerce *post-implementatie wordt overgeslagen omdat implementatie is mislukt* fout
description: 'Dit artikel legt uit hoe u een implementatiefout kunt onderzoeken: *Post-Implementatie wordt overgeslagen omdat implementatie is mislukt*'
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Adobe Commerce *post-opstellen wordt overgeslagen omdat opstellen* fout ontbrak

Dit artikel verklaart hoe te om een plaatsingsfout te onderzoeken: *Post-stelt wordt overgeslagen omdat opstellen* ontbrak die tijdens plaatsing aan verschillende milieu&#39;s voorkomt, bijvoorbeeld bevordering.

## Betrokken producten en versies

Adobe Commerce op wolkeninfrastructuur [ alle gesteunde versies ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

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

Om het foutenspoor voor het bepalen van de daadwerkelijke oorzaak te verkrijgen, SSH aan de server en controleer het logboekdossier `var/log/install_upgrade.log`.
