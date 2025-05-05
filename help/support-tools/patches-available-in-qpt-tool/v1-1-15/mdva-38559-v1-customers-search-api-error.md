---
title: 'MDVA-38559: /V1/customer/search API retourneert een fout'
description: De patch MDVA-38559 verhelpt het probleem waarbij de API &grave;/V1/customer/search&grave; een fout retourneert voor klanten met meer dan één abonnement. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-38559. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 434fe78c-c384-4fa8-b26a-cb00007e490e
feature: REST, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-38559: /V1/customer/search API retourneert een fout

De MDVA-38559-patch verhelpt het probleem waarbij de `/V1/customers/search` -API een fout retourneert voor klanten met meer dan één abonnement. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 geïnstalleerd is. De patch-id is MDVA-38559. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`/V1/customers/search` API retourneert een fout voor klanten met meer dan één abonnement.

<u> Eerste vereisten </u>:

De Adobe Commerce-winkel gebruikt meerdere websites.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > **Configuratie** > **Klant** > **de Configuratie van de Klant** > **de Opties van het Delen van de Rekening** en selecteer **Globaal**.
1. Ga naar **Klanten** > **Alle Klanten**, uitgezocht **geef** op om het even welke klant uit, en selecteer dan **Nieuwsbrief**.
1. Abonneer u op een nieuwsbrief voor meerdere websites en sla de klant op.
1. Verzend het volgende verzoek:

```REST API
V1/customers/search?searchCriteria[filterGroups][0][filters][0][field]=email&searchCriteria[filterGroups][0][filters][0][value]=test@example.com&searchCriteria[filterGroups][0][filters][0][conditionType]=eq
```

<u> Verwachte resultaten </u>:

De zoekresultaten van de klant worden weergegeven.

<u> Ware resultaten </u>:

De volgende fout wordt geregistreerd aan exception.log: *Punt (Magento\Customer\Model\Customer\Interceptor) met zelfde identiteitskaart &quot;1&quot;bestaat reeds.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
