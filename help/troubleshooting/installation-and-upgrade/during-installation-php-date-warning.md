---
title: Waarschuwing PHP-datum tijdens installatie
description: Dit artikel bevat een correctie voor een PHP-datumwaarschuwing tijdens de installatie.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# Waarschuwing PHP-datum tijdens installatie

Dit artikel bevat een correctie voor een PHP-datumwaarschuwing tijdens de installatie.

## Details {#details}

Tijdens de installatie wordt het volgende bericht weergegeven:

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### Oplossing {#solution}

Controleer de instelling van de PHP tijdzone zorgvuldig. Verwijs naar [ Gids van de Installatie > PHP Montages ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) in onze ontwikkelaarsdocumentatie.
