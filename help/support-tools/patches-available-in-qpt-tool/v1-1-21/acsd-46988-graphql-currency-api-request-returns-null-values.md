---
title: 'ACSD-46988: GraphQL currency API request returns null values'
description: De ACSD-46988-patch verhelpt het probleem waarbij de GraphQL API-aanvraag null-waarden retourneert voor een aangepaste valuta. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 is geïnstalleerd. De patch-id is ACSD-46988. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 8da0ab99-8db9-4222-9400-6df1520267f0
feature: REST, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-46988: GraphQL API-aanvraag retourneert null-waarden

De ACSD-46988-patch verhelpt het probleem waarbij de GraphQL API-aanvraag null-waarden retourneert voor een aangepaste valuta. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 is geïnstalleerd. De patch-id is ACSD-46988. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aanvraag voor API voor GraphQL-valuta retourneert null-waarden voor een aangepaste valuta.

<u>Stappen om te reproduceren</u>:

1. Aangepaste valuta configureren in de Admin. Ga naar **Systeem** > **Configuratie** > **Algemeen** > **Valuta-instelling**.
1. Verzend een GraphQL-aanvraag met de volgende payload:

<pre>
<code class="language-graphql">
{
    currency {
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates {
            currency_to
            rate
        }
    }
}
</code>
</pre>

<u>Verwachte resultaten</u>:

De aanvraag retourneert valutawaarden in plaats van null-waarden.

<u>Werkelijke resultaten</u>:

De aanvraag retourneert meerdere null-waarden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding voor het gereedschap Kwaliteitspatches.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Aanvullende stappen vereist na de installatie van de patch

Voor gebruikers ter plaatse:

* Uitvoeren: `composer require symfony/intl:"~5.4.11"`

Voor gebruikers van Cloud:

* Uitvoeren: `composer require symfony/intl:"~5.4.11"`
* Push `composer.json` en `composer.lock` samen met het patchbestand naar de opslagplaats van de kit.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de handleiding voor het gereedschap Kwaliteitspatches.
