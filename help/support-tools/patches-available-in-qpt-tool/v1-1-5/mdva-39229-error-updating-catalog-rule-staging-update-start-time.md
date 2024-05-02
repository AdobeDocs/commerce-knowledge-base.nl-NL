---
title: 'MDVA-39229: Fout na het bijwerken van de Catalogusregel Staging update start time'
description: De patch MDVA-39229 verhelpt het probleem waarbij gebruikers een fout krijgen na het bijwerken van de begintijd van de update voor het stapelen van catalogusregels. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 is geïnstalleerd. De patch-id is MDVA-39229. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229: Fout na het bijwerken van de regel van de Catalogus het Staging update begintijd

De patch MDVA-39229 verhelpt het probleem waarbij gebruikers een fout krijgen na het bijwerken van de begintijd van de update voor het stapelen van catalogusregels. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 is geïnstalleerd. De patch-id is MDVA-39229. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.3.4-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers krijgen een fout na het bijwerken van de begintijd van de update voor het instellen van catalogusregels.

<u>Stappen om te reproduceren</u>:

1. Maak een regel voor catalogusprijzen.
1. Maak en voer een eventuele testupdate voor het trapsgewijs opvoeren uit.
1. Voer de query uit en controleer of de vlag Staging is gemaakt.


   `select * from flag;`


1. Maak een nieuwe Staging-update die na vijf minuten start.
1. Openen **Inhoud** > **Staging** > **Dashboard** > **Nieuwe update** en vertragen de begintijd met één minuut.
1. Wacht zes minuten.
1. Uitsnijden uitvoeren.

<u>Verwachte resultaten</u>:

De begintijd van de update wordt gewijzigd en de update wordt toegepast. De oude update wordt verwijderd uit het dialoogvenster `staging_update` tabel.

<u>Werkelijke resultaten</u>:

Gebruikers krijgen de volgende fout:

*report.ERROR: Cron Job staging_synchronize_entities_period heeft een fout: de actieve update kan niet worden verwijderd.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
