---
title: Fout "'Gebiedscode is niet ingesteld'' bij het uitvoeren van setup:upgrade'
description: Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met de cloudinfrastructuur 2.2.3 met betrekking tot de *Area-code is niet ingesteld*-fout wanneer de opdracht setup:upgrade wordt uitgevoerd.
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
source-git-commit: 4617b915a62093e00da428a753d913a39d30f3a0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Fout bij uitvoeren van &#39;Gebiedscode is niet ingesteld&#39; `setup:upgrade`

Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.3 dat verband houdt met het ophalen van de *&quot;Gebiedscode is niet ingesteld&quot;* fout bij het uitvoeren van de volgende opdracht:

```bash
setup:upgrade
```

>[!NOTE]
>
>Het probleem is opgelost in Adobe Commerce 2.2.4.

## Probleem

Wanneer u het

```bash
bin/magento setup:upgrade
```

krijgt u het volgende foutbericht: *&quot;Module &#39;Magento\_AdvancedSalesRule&#39;: Gegevens installeren...Gebiedscode niet ingesteld: Gebiedscode moet worden ingesteld voordat een sessie wordt gestart&quot;* en de uitvoering van de opdracht wordt onderbroken. De kwestie verschijnt omdat de gebiedsconfiguratie wordt gevraagd alvorens het eigenlijk wordt geplaatst. De patch maakt het mogelijk de fout op te vangen en het upgradeproces niet te onderbreken.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch downloaden](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce over wolkeninfrastructuur 2.2.3

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.2.0 - 2.2.3

## Hoe de pleister aanbrengen

Zie voor instructies [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning.

## Bijgevoegde bestanden
