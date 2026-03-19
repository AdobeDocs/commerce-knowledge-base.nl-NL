---
title: Implementatiefouten waarbij patches niet zijn gevonden
description: 'Dit artikel biedt een oplossing voor het probleem waarbij een fout *Volgende patches niet zijn gevonden: MDVA-XXXXX, ACSD-XXXXX. Controleer of deze patches voor de huidige Magento-versie* beschikbaar zijn via de opdracht ''status''.'
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: 724a30310c3841f8280628436925f9a3e5933b14
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Implementatiefouten waarbij patches niet zijn gevonden

Dit artikel verstrekt een oplossing aan de kwestie wanneer het bevorderen van uw instantie ontbreekt de plaatsing en u ziet een fout in de plaatsingslogboeken: *Volgende flarden werden niet gevonden: MDVA-XXXXX, ACSD-XXXXX. Gelieve te controleren met &quot;status&quot;bevelbeschikbaarheid van deze flarden voor de huidige versie van Magento*.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, [&#x200B; alle gesteunde versies &#x200B;](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## Probleem

U ervaart een fout wanneer het bevorderen van Adobe Commerce: *Volgende flarden werden niet gevonden*.

## Oorzaak

Eerder toegepaste patches voor uw oudere versie(s) zijn niet van toepassing of zijn niet meer beschikbaar voor uw nieuwe versie.

## Oplossing

1. Controleer het `.magento.env.yaml` -bestand onder de sectie QUALITY_PATCHES, bijvoorbeeld:

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. Zoek omhoog de flardidentiteitskaarts in de [&#x200B; Nota&#39;s van de Versie van de Patches van de Kwaliteit &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html?lang=nl-NL) om te controleren of elke één op de nieuwe versie van Adobe Commerce kan worden toegepast u bevordert aan.
1. Als de patch niet van toepassing is op de nieuwe versie van Adobe Commerce waarnaar u wilt upgraden, verwijdert u de patch-id uit het `.magento.env.yaml` -bestand.
1. Als u alle patch-id&#39;s hebt gecontroleerd die door de fout worden aangegeven, duw dan op de wijzigingen en wijzig de implementatie.

## Gerelateerde lezing

* [&#x200B; past flarden &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL#apply-a-patch-in-a-local-environment) in Commerce op de Gids van de Infrastructuur van de Wolk toe.
