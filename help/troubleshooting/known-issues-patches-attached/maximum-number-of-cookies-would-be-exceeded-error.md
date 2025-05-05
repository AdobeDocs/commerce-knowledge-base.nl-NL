---
title: Fout bij maximum aantal cookies in Adobe Commerce
description: Leer hoe u het Adobe Commerce-probleem kunt oplossen waarbij een fout optreedt waarbij het maximumaantal cookies wordt overschreden.
feature: Deploy, Support, Upgrade, Tools and External Services
role: Admin, Developer
source-git-commit: 44e167c801bbcd313f74c9fc51f9cde9473ef96f
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# *Maximum aantal koekjes zou* fout in Adobe Commerce worden overschreden

Dit artikel verstrekt flarden om de fout op te lossen die *Maximum aantal koekjes verklaren* in Adobe Commerce zou worden overschreden.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7, met een van de volgende patches:

* MDVA-12304-patch toegepast met de [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/release-notes)
* [APSB25-08 geïsoleerde beveiligingspatch](/help/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08.md)
* [ de Patches van de Wolk voor  [!DNL Commerce]  1.1.4 ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)

## Probleem

Vanwege problemen met cookies in Adobe Commerce wordt de volgende fout weergegeven in de foutlogboeken:

*report.WARNING: Onbekwaam om het koekje te verzenden. Het maximum aantal cookies wordt overschreden.*

### Oorzaak

De kwestie komt voor omdat het maximumaantal toegestane koekjes aan *50* wordt geplaatst.

## Oplossing

1. Verwijder de MDVA-12304-patch als u deze met de [!DNL Quality Patches Tool (QPT)] toepaste.

   * Voor Adobe Commerce op cloudinfrastructuur verwijdert u de patch uit `.magento.env.yaml` .
   * Voor Adobe Commerce-installaties op locatie voert u de volgende opdracht uit om de patch te herstellen:

     `vendor/bin/magento/quality-patches revert MDVA-12304`

1. Pas de bijgevoegde patches toe volgens uw Adobe Commerce-versie:

   * Voor versies 2.4.4-p12, 2.4.5-p11, 2.4.6-p9 en 2.4.7-p4, pas [ ACSD-64710 flard ](assets/acsd-64710_2.4.5-p11.patch.zip) toe.

   * Voor versies 2.4.4-p13, 2.4.5-p12, 2.4.6-p10, 2.4.7-p5 en 2.4.8, pas [ ACSD-65562 flard ](assets/acsd-65562_2.4.5-p12.patch.zip) toe.

### Gerelateerde lezing

* [ past flarden ](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/patches/apply) in de gids van de Verbetering van Adobe Commerce toe
* [ Beste praktijken voor het verspreiden van de flarden van Adobe Commerce bij schaal ](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale) in het Playbook van de Implementatie van Adobe Commerce
* [ de nota&#39;s van de Versie voor Commerce Cloud Tools Suite ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) in Commerce op de Gids van de Wolk.
