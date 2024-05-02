---
title: 'MDVA-38559: /V1/customer/search API returns error'
description: De patch MDVA-38559 verhelpt het probleem waarbij de API `/V1/customer/search` een fout retourneert voor klanten met meer dan één abonnement. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-38559. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 434fe78c-c384-4fa8-b26a-cb00007e490e
feature: REST, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-38559: /V1/customer/search API retourneert een fout

De MDVA-38559-patch verhelpt het probleem waarbij de `/V1/customers/search` API retourneert een fout voor klanten met meer dan één abonnement. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-38559. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`/V1/customers/search` API retourneert een fout voor klanten met meer dan één abonnement.

<u>Vereisten</u>:

De Adobe Commerce-winkel gebruikt meerdere websites.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkel** > **Configuratie** > **Klant** > **Klantconfiguratie** > **Opties voor het delen van accounts** en selecteert u **Algemeen**.
1. Ga naar **Klanten** > **Alle klanten**, selecteert u **Bewerken** op om het even welke klant, en selecteer dan **Nieuwsbrief**.
1. Abonneer u op een nieuwsbrief voor meerdere websites en sla de klant op.
1. Verzend het volgende verzoek:

```REST API
V1/customers/search?searchCriteria[filterGroups][0][filters][0][field]=email&searchCriteria[filterGroups][0][filters][0][value]=test@example.com&searchCriteria[filterGroups][0][filters][0][conditionType]=eq
```

<u>Verwachte resultaten</u>:

De zoekresultaten van de klant worden weergegeven.

<u>Werkelijke resultaten</u>:

De volgende fout wordt geregistreerd aan exception.log: *Item (Magento\Customer\Model\Customer\Interceptor) met dezelfde id &quot;1&quot; bestaat al.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
