---
title: 'MDVA-30599: customer_is_gast is onjuist ingesteld'
description: De patch MDVA-30599 verhelpt de kwestie waar de gastcitaten die met API worden gecreeerd verkeerd als citaten voor het programma geopende klanten worden gemerkt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.4.2.
exl-id: e16bb926-241b-451e-89a5-33000f73c5b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-30599: customer_is_gast wordt verkeerd geplaatst

De patch MDVA-30599 verhelpt de kwestie waar de gastcitaten die met API worden gecreeerd verkeerd als citaten voor het programma geopende klanten worden gemerkt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.0

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gastcitaten die zijn gemaakt met API worden onjuist gemarkeerd als aanhalingstekens voor aangemelde klanten.

<u>Stappen om te reproduceren</u>:

1. Voeg in de Adobe Commerce-winkel een product als gastgebruiker toe aan de winkelwagen.
1. Zoek in de Adobe Commerce DB naar de bijbehorende `quote_id_mask`.
1. Een API-aanvraag verzenden naar `quoteGuestCartRepositoryV1` Interface voor opslagplaats voor winkelwagentjes. Dit kan via Swagger of cURL-verzoek worden gedaan.

```curl
curl -X GET "http://web2-73.sparta.corp.magento.com/dev/support/ee24dev/rest/all/V1/guest-carts/ToOwPtSBxkorkCLq6ztwupPd99y8zhky" -H "accept: application/json"
```

<u>Verwachte resultaten</u>:

Als reactie krijg je `"customer_is_guest": true`

<u>Werkelijke resultaten</u>:

Als reactie krijg je `"customer_is_guest": false`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Aanvullende stappen vereist na de installatie van de patch

De patch is effectief voor alle nieuwe gastwinkelwagentjes. Als u bestaande gastwinkelwagentjes moet herstellen, stelt u `quote.customer_is_guest = 1` voor die registers `quote.customer_id` is NULL. U zou een vraag kunnen in werking stellen gelijkend op het volgende:

```sql
UPDATE quote SET customer_is_guest = 1 WHERE customer_id IS NULL;
```

>[!WARNING]
>
>Wij adviseren sterk het testen van de vraag op het Staging/de milieu van de Integratie alvorens het in Productie in werking te stellen. Wij adviseren ook om een recente steun te hebben alvorens om het even welke manipulaties met OB.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
