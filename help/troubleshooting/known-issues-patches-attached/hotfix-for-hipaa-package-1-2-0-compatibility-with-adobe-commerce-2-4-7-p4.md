---
title: Adobe Commerce 2.4.7-p4  [!DNL HIPAA]  1.2.0 verenigbaarheidspakket Hotfix
description: Dit artikel verstrekt hotfix om verenigbaarheid voor het nieuwe  [!DNL HIPAA]  pakket 1.2.0 met Adobe Commerce op de infrastructuur van de Wolk 2.4.7-p4 toe te voegen
feature: Install, Upgrade, Security, Compliance
role: Developer
source-git-commit: 705c43d2328d47fb5f00ae582a2a623ca9f94f70
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0-compatibiliteitspakket Hotfix

Dit artikel biedt een hotfix om compatibiliteit voor het nieuwe **[!DNL HIPAA]-pakket 1.2.0** toe te voegen met Adobe Commerce on Cloud Infrastructure 2.4.7-p4.

Het probleem wordt opgelost in de versie 2.4.7-p5.

## Betrokken versies en producten

Adobe Commerce on Cloud Infrastructure 2.4.7-p4 en eerdere versies

## Vereisten

* Adobe heeft uw Adobe Commerce-account ingericht voor toegang tot de extensie **[!DNL HIPAA Ready]** . Zie [[!DNL HIPAA]  bereidheid op Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) voor meer details in onze **Adobe Commerce: Begonnen Gids** krijgen.
* Toegang tot [ repo.magento.com ](https://repo.magento.com) om de uitbreiding te installeren. Voor zeer belangrijke generatie en het verkrijgen van de noodzakelijke rechten, zie [ uw authentificatiesleutels ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) in onze **Adobe Commerce krijgen: De Gids van de Installatie**.

## Probleem

Het [!DNL HIPAA] -pakket 1.1.0 is niet compatibel met de releaselijn van Adobe Commerce 2.4.7x.

## Oplossing

Via deze hotfix kunnen handelaren die Adobe Commerce uitvoeren op Cloud Infrastructure 2.4.7-p4 het [!DNL HIPAA] -pakket 1.2.0 gebruiken.

>[!NOTE]
>
>**[!DNL HIPAA]1.2.0 is alleen compatibel met Adobe Commerce 2.4.7-p5. Installeer de meegeleverde patch als u compatibiliteit met [!DNL HIPAA] 1.2.0 wilt toevoegen aan Adobe Commerce 2.4.7-p4.<br><u> als u niet op Adobe Commerce 2.4.7-p4 bent, moet u eerst aan Adobe Commerce 2.4.7-p4 bevorderen om dit flard </u> te gebruiken.**

Als u het probleem voor Adobe Commerce op Cloud Infrastructure 2.4.7-p4 wilt verhelpen, past u de patch toe:

[ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip](assets/ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip)

## Hoe de pleister aanbrengen

Pak het dossier uit en zie [ hoe te om een componentenflard toe te passen die door Adobe ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in onze basis van steunkennis voor instructies wordt verstrekt.

## Alleen voor Adobe Commerce op Cloud-handelaren - Hoe weet u of de patch is toegepast

Aangezien het niet mogelijk is om gemakkelijk te controleren of de kwestie werd gepatcheerd, zou u kunnen willen controleren of de flard met succes is toegepast.

>[!NOTE]
>
><u> u kunt dit doen door deze stappen te volgen, gebruikend het dossier `VULN-27015-2.4.7_COMPOSER.patch` **als Voorbeeld**</u>:

1. [ installeer het Hulpmiddel van de Patches van de Kwaliteit ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Voer de opdracht uit:<br>
   ![ cve-2024-34102-tell-if-patch-applied-code ](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. U zou output gelijkend op dit moeten zien, **<u>waar het hier gebruikte Voorbeeld, VULN-27015</u>**, de *Toegepaste* status terugkeert:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->
