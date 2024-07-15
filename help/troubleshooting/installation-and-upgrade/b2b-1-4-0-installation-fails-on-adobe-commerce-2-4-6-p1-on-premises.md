---
title: '[!DNL B2B] 1.4.0-installatie mislukt op Adobe Commerce 2.4.6-p1 op locatie'
description: Dit artikel verstrekt een oplossing voor Adobe Commerce 2.4.6-p1 op-gebouw kwestie waar  [!DNL B2B]  versie 1.4.0 installatie ontbreekt.
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# De installatie van [!DNL B2B] 1.4.0 mislukt op Adobe Commerce 2.4.6-p1 in bedrijven

Dit artikel biedt een oplossing voor het probleem dat zich op locatie bij Adobe Commerce 2.4.6-p1 voordoet en waarbij de installatie van [!DNL B2B] versie 1.4.0 mislukt.

## Betrokken producten en versies

* Adobe Commerce 2.4.6-p1 **op-gebouw**
* [!DNL B2B] versie 1.4.0

>[!NOTE]
>
>[!DNL B2B] versie 1.4.0 met succes installeert op **Adobe Commerce Cloud 2.4.6-p1**.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Installeer Adobe Commerce 2.4.6-p1.

   ```terminal
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. Installeer [!DNL B2B] versie 1.4.0.

   ```terminal
   composer require magento/extension-b2b:1.4.0
   ```

<u> Verwachte resultaten </u>:

Met [!DNL B2B] versie 1.4.0 kan worden geïnstalleerd op Adobe Commerce 2.4.6-p1.

<u> Ware resultaten </u>:

Installatie mislukt met de onderstaande fout:

```terminal
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## Workaround

Met succes installeren of bevorderen aan [!DNL B2B] versie 1.4.0 op Adobe Commerce 2.4.6-p1 door handgebiedsdelen voor het [!DNL B2B] veiligheidspakket met a [ stabiliteitmarkering ](https://getcomposer.org/doc/04-schema.md#package-links) toe te voegen.

1. Werk `composer.json` vanuit de installatiemap van Adobe Commerce bij met de vereiste afhankelijkheden:

   ```terminal
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **output van het Bevel:**

   ```terminal
   Running composer update magento/module-re-captcha-company magento/security-package-b2b
   Loading composer repositories with package information
   Updating dependencies
   Lock file operations: 2 installs, 0 updates, 0 removals
     - Locking magento/module-re-captcha-company (1.0.3-beta1)
     - Locking magento/security-package-b2b (1.0.4-beta1)
   Writing lock file
   Installing dependencies from lock file (including require-dev)
   Package operations: 2 installs, 0 updates, 0 removals
     - Downloading magento/module-re-captcha-company (1.0.3-beta1)
     - Installing magento/module-re-captcha-company (1.0.3-beta1): Extracting archive
     - Installing magento/security-package-b2b (1.0.4-beta1)
   1 package suggestions were added by new dependencies, use `composer suggest` to see details.
   Package sebastian/phpcpd is abandoned, you should avoid using it. No replacement was suggested.
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Werk `composer.json` bij om [!DNL B2B] versie 1.4.0 toe te voegen.

   ```terminal
   composer require magento/extension-b2b=1.4.0
   ```

   **output van het Bevel:**

   ```terminal
   ./composer.json has been updated
   Running composer update magento/extension-b2b
   Loading composer repositories with package information
   Updating dependencies
   ...
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Voltooi het installatie- of upgradeproces.

   * [ installeer  [!DNL B2B]  op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html)
   * [ installeer op-gebouw ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html)
