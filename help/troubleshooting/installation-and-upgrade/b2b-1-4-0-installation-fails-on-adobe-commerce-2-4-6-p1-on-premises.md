---
title: '[!DNL B2B] 1.4.0 de installatie ontbreekt op Adobe Commerce 2.4.6-p1 op-gebouw'
description: Dit artikel biedt een oplossing voor de Adobe Commerce 2.4.6-p1-kwestie op locatie waar [!DNL B2B] De installatie van versie 1.4.0 is mislukt.
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# [!DNL B2B] 1.4.0 de installatie ontbreekt op Adobe Commerce 2.4.6-p1 op gebouw

Dit artikel biedt een oplossing voor de Adobe Commerce 2.4.6-p1-kwestie op locatie waar [!DNL B2B] De installatie van versie 1.4.0 is mislukt.

## Betrokken producten en versies

* Adobe Commerce 2.4.6-p1 **ter plaatse**
* [!DNL B2B] versie 1.4.0

>[!NOTE]
>
>[!DNL B2B] versie 1.4.0 kan worden geïnstalleerd op **Adobe Commerce Cloud 2.4.6-p1**.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Installeer Adobe Commerce 2.4.6-p1.

   ```terminal
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. Probeer te installeren [!DNL B2B] versie 1.4.0.

   ```terminal
   composer require magento/extension-b2b:1.4.0
   ```

<u>Verwachte resultaten</u>:

[!DNL B2B] Versie 1.4.0 wordt geïnstalleerd op Adobe Commerce 2.4.6-p1.

<u>Werkelijke resultaten</u>:

Installatie mislukt met de onderstaande fout:

```terminal
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## Workaround

Installeren of upgraden naar [!DNL B2B] versie 1.4.0 op Adobe Commerce 2.4.6-p1 door handmatige afhankelijkheden voor de [!DNL B2B] beveiligingspakket met [stabiliteitstag](https://getcomposer.org/doc/04-schema.md#package-links).

1. Bijwerken vanuit de Adobe Commerce-installatiemap `composer.json` met de vereiste afhankelijkheden:

   ```terminal
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **Uitvoer opdracht:**

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

1. Bijwerken `composer.json` toevoegen [!DNL B2B] versie 1.4.0.

   ```terminal
   composer require magento/extension-b2b=1.4.0
   ```

   **Uitvoer opdracht:**

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

   * [Installeren [!DNL B2B] over cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html)
   * [Installeren in de bedrijfsruimten](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html)
