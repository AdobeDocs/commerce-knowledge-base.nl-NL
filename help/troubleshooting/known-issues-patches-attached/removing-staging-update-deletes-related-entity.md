---
title: Als u een gefaseerde update verwijdert, verwijdert u gerelateerde entiteit
description: Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.3-probleem met betrekking tot de entiteit (categorie, CMS-pagina, enz.) zelf wordt verwijderd wanneer de gerelateerde update van het schema wordt verwijderd.
exl-id: 91138ac1-916e-4dd1-bad5-892524fdd9e1
feature: CMS, Cache, Categories, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Als u een gefaseerde update verwijdert, verwijdert u gerelateerde entiteit

Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.3-probleem met betrekking tot de entiteit (categorie, CMS-pagina, enz.) zelf wordt verwijderd wanneer de gerelateerde update van het schema wordt verwijderd.

>[!NOTE]
>
>Het probleem is opgelost in Adobe Commerce 2.2.6.

## Probleem

Wanneer u een actieve planningsupdate verwijdert tussen de begin- en einddatum, wordt de verwante entiteit (categorie, subcategorie, CMS-pagina) ook verwijderd.

<u>Stappen om te reproduceren (met categorieën)</u>:

1. Meld u aan bij de Commerce-beheerder.
1. Een nieuwe subcategorie maken onder **Catalogus** > **Categorieën**.
1. Maak een nieuwe testupdate met de begin- en eindtijd.
1. Wacht tot de update wordt toegepast; dat is de begintijd komt.
1. De update verwijderen met de opdracht **Weergeven/bewerken** koppeling.

<u>Verwachte resultaten</u>:

De update wordt verwijderd en de subcategorie bestaat nog steeds in Beheer.

<u>Werkelijke resultaten</u>:

De update en de subcategorie worden verwijderd.

## Oplossing

Pas de patch toe die in dit artikel is voorzien en wis de cache actief

```bash
bin/magento
  cache:clean
```

## Reparatie

De patches zijn aan dit artikel gekoppeld. Als u een patch wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de bijbehorende koppeling:

* [MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch downloaden](assets/MDVA-11059_EE_2.2.3_COMPOSER_v1.patch.zip)
* [Download MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-23505_EE_2.2.4_COMPOSER_v1.patch.zip)
* [MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch downloaden](assets/MDVA-12158_EE_2.2.5_COMPOSER_v2.patch.zip)

### Compatibele Adobe Commerce-versies:

De patches zijn gemaakt voor:

* MDVA-1059\_EE\_2.2.3\_COMPOSER\_v1.patch is gemaakt voor Adobe Commerce (alle implementatiemethoden) 2.2.3
* MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch is gemaakt voor Adobe Commerce (alle implementatiemethoden) 2.2.4
* MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch is gemaakt voor Adobe Commerce (alle implementatiemethoden) 2.2.5

De patch MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op locatie 2.2.0-2.2.2
* Adobe Commerce over cloudinfrastructuur 2.2.0-2.2.3

De patch MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op locatie 2.1.0-2.1.18, 2.2.0-2.2.3
* Adobe Commerce op cloudinfrastructuur 2.1.0-2.1.18, 2.2.0-2.2.3

De patch MDVA-23505\_EE\_2.2.5\_COMPOSER\_v1.patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce over wolkeninfrastructuur 2.2.5

## Hoe de pleister aanbrengen

Zie [Een door Adobe Commerce geleverde componentpatch toepassen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies.

## Bijgevoegde bestanden
