---
title: De opdracht voor het installeren van de composer overschrijft het .gitignore-bestand, Adobe Commerce
description: Dit artikel biedt een oplossing voor het geval dat een bijgehouden `.gitignore'-bestand wordt overschreven door composer op Adobe Commerce op cloudinfrastructuur 2.4.2-p1 en 2.3.7.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# De opdracht voor het installeren van de composer overschrijft het .gitignore-bestand, Adobe Commerce

Dit artikel biedt een oplossing voor het geval een track `.gitignore` bestand wordt overschreven door composer op Adobe Commerce op cloudinfrastructuur 2.4.2-p1 en 2.3.7.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.4.2-p1 en 2.3.7.

## Probleem

`.gitignore` bestand wordt overschreven wanneer de opdracht voor het installeren van composer wordt uitgevoerd.

<u>Stappen om te reproduceren</u>:


1. Maak een lege map voor de werkruimte.
1. Voer deze opdracht uit in de hoofdmap:

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition:2.4.2-p1.
   ```

   \# of 2.3.7

1. Voer vervolgens de volgende opdrachten uit:
   1. `echo "/this/line/should/stay" >> .gitignore`
   1. `git init`
   1. `git add * && git add .*`
   1. `git commit -m "Init"` # bestand dat moet worden gerepareerd
   1. `rm -rf vendor/*`
   1. `composer install`
   1. `git diff`

      ```git
      diff --git a/.gitignore b/.gitignore
      index c144521..7092a56 100644
      --- a/.gitignore
      +++ b/.gitignore
      @@ -70,4 +70,3 @@ atlassian*
      /generated/*
      !/generated/.htaccess
      .DS_Store
      -/this/line/should/stay
      ```

<u>Verwacht resultaat</u>:

`.gitignore` wordt niet overschreven door composer.

<u>Werkelijk resultaat</u>:

`.gitignore` wordt overschreven door elke installatie van de composer.

## Oplossing

Aangepaste `.gitignore file` u moet het in `magento-deploy-ignore` sectie.

```git
{
...
"extra": {
    "magento-deploy-ignore": {
        "*": [
            "/.gitignore"
        ]
    }
    ...
}
```


## Gerelateerde lezing

* [Het getraceerde .gitignore-bestand wordt overschreven door de componist!](https://github.com/magento/magento2/issues/32888) in Magento2 GitHub.
