---
title: Googles Analytics volgen geen conversiegegevens
description: Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.4-probleem met betrekking tot Googles Analytics die de conversiegegevens niet bijhouden.
exl-id: b9012fd1-4f90-41e9-9559-0343ee052ec6
feature: Configuration, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Googles Analytics volgen geen conversiegegevens

Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.4-probleem met betrekking tot Googles Analytics die de conversiegegevens niet bijhouden.

>[!NOTE]
>
>Het probleem is opgelost in Adobe Commerce 2.2.6.

## Probleem

De conversiegegevens zijn niet bijgehouden door Googles Analytics vanwege een fout in de code van de component Googles Analytics.

<u>Stappen om te reproduceren</u>:

1. De functionaliteit Googles Analytics in Commerce Admin inschakelen en configureren onder **Winkels** > **Instellingen** > **Configuratie** > **Verkoop** > **GOOGLE API** > **Googles Analytics**.
1. Klikken **Config opslaan**.
1. Plaats een bestelling op de winkel.
1. Ga naar **Dashboard Googles Analytics** > **Conversies** > **Overzicht**.
1. Stel het datumbereik in op de huidige datum.

<u>Verwacht resultaat</u>:

De volgorde wordt weergegeven in de conversiegegevens.

<u>Werkelijk resultaat</u>:

De volgorde wordt niet weergegeven in de conversiegegevens.

## Oplossing

De patch corrigeert de fout in de code van de Googles Analytics component. Nadat de patchconversiegegevens zijn toegepast, worden deze door Googles Analytics bijgehouden.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[Download MDVA-11263\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-11263_EE_2.2.4_v1.composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce op locatie 2.2.4

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op locatie 2.2.5
* Adobe Commerce over wolkeninfrastructuur 2.2.4, 2.2.5

## Hoe de pleister aanbrengen

Zie [Een door Adobe Commerce geleverde componentpatch toepassen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies.

## Bijgevoegde bestanden
