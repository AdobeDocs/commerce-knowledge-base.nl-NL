---
title: "MDVA-42806: Nieuwe e-mail voor de registratie van bedrijven wordt verzonden telkens wanneer een bestaande onderneming wordt bijgewerkt"
description: Met de MDVA-42806-patch wordt het probleem opgelost waarbij telkens een nieuwe bedrijfsregistratie-e-mail wordt verzonden wanneer een bestaand bedrijf via REST API wordt bijgewerkt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-42806. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 957b89f7-cd4d-4c94-8d1d-c30442aafa6a
feature: REST, B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-42806: Nieuwe e-mail voor bedrijfsregistratie wordt verzonden telkens wanneer een bestaande onderneming wordt bijgewerkt

Met de MDVA-42806-patch wordt het probleem opgelost waarbij telkens een nieuwe bedrijfsregistratie-e-mail wordt verzonden wanneer een bestaand bedrijf via REST API wordt bijgewerkt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-42806. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Telkens wanneer een bestaand bedrijf via de REST API wordt bijgewerkt, wordt er een nieuwe bedrijfsregistratie-e-mail verzonden.

<u>Vereisten</u>:

B2B-modules geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Maak een bedrijfsaccount.
1. Gebruiken `/V1&#x200B;/company&#x200B;/<company_id>` eindpunt. Als u het gemaakte bedrijf wilt bijwerken, raadpleegt u [het bedrijf bijwerken](https://devdocs.magento.com/guides/v2.4/b2b/company-object.html#update-the-company) in onze ontwikkelaarsdocumentatie. Hieronder ziet u een voorbeeld van een lading:

```php
{
    "company": {
        "id": 2,
        "status": 1,
        "company_name": "Company",
        "company_email": "company@example.test",
        "street": [
            "Test"
        ],
        "city": "Test",
        "country_id": "US",
        "region_id": "1",
        "postcode": "12345",
        "telephone": "8009994301",
        "customer_group_id": 2,
        "sales_representative_id": 1,
        "super_user_id": 2
    }
}
```

<u>Verwachte resultaten</u>:

Er wordt geen e-mail verzonden met de melding &quot;New company registration request&quot; (Nieuwe aanvraag voor bedrijfsregistratie) omdat de API een bestaand bedrijf bijwerkt.

<u>Werkelijke resultaten</u>:

Elke keer dat de API-aanvraag wordt verzonden, wordt een e-mail verzonden met de melding &quot;Nieuwe aanvraag voor bedrijfsregistratie&quot;.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
