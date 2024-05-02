---
title: Implementatiefouten waarbij patches niet zijn gevonden
description: "Dit artikel biedt een oplossing voor het probleem waarbij een fout *De volgende patches zijn niet gevonden: MDVA-XXXXX, ACSD-XXXXX. Controleer of deze patches beschikbaar zijn voor de huidige versie van het Magento*."
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Implementatiefouten waarbij patches niet zijn gevonden

Dit artikel verstrekt een oplossing aan de kwestie wanneer de bevordering van uw instantie ontbreekt de plaatsing en u ziet een fout in de plaatsingslogboeken: *Er zijn geen volgende patches gevonden: MDVA-XXXXX, ACSD-XXXXX. Controleer of deze patches voor de huidige versie van het Magento beschikbaar zijn voor de opdracht status*.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## Probleem

Er is een fout opgetreden bij het upgraden van Adobe Commerce: *De volgende patches zijn niet gevonden*.

## Oorzaak

Eerder toegepaste patches voor uw oudere versie(s) zijn niet van toepassing of zijn niet meer beschikbaar voor uw nieuwe versie.

## Oplossing

1. Controleer uw `.magento.env.yaml` bestand onder de sectie QUALITY_PATCH, bijvoorbeeld

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. De patch-id&#39;s opzoeken in het dialoogvenster [Opmerkingen bij de release Kwaliteitspatches](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) om te controleren of elke versie kan worden toegepast op de nieuwe versie van Adobe Commerce waarnaar u de upgrade uitvoert.
1. Als de patch niet van toepassing is op de nieuwe versie van Adobe Commerce waarnaar u wilt upgraden, verwijdert u de patch-id uit het dialoogvenster `.magento.env.yaml` bestand.
1. Als u alle patch-id&#39;s hebt gecontroleerd die door de fout worden aangegeven, duw dan op de wijzigingen en wijzig de implementatie.

## Gerelateerde lezing

* [Patches toepassen](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) in Commerce on Cloud Infrastructure Guide.
