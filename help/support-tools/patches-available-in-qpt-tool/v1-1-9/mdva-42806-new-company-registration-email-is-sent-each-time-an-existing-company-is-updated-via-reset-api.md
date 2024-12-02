---
title: 'MDVA-42806: Nieuwe e-mail voor bedrijfsregistratie wordt verzonden telkens wanneer een bestaande onderneming wordt bijgewerkt'
description: Met de MDVA-42806-patch wordt het probleem opgelost waarbij telkens een nieuwe bedrijfsregistratie-e-mail wordt verzonden wanneer een bestaand bedrijf via REST API wordt bijgewerkt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-42806. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 957b89f7-cd4d-4c94-8d1d-c30442aafa6a
feature: REST, B2B, Communications, Companies
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-42806: Nieuwe e-mail voor bedrijfsregistratie wordt verzonden telkens wanneer een bestaande onderneming wordt bijgewerkt

Met de MDVA-42806-patch wordt het probleem opgelost waarbij telkens een nieuwe bedrijfsregistratie-e-mail wordt verzonden wanneer een bestaand bedrijf via REST API wordt bijgewerkt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 geïnstalleerd is. De patch-id is MDVA-42806. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Telkens wanneer een bestaand bedrijf via de REST API wordt bijgewerkt, wordt er een nieuwe bedrijfsregistratie-e-mail verzonden.

<u> Eerste vereisten </u>:

B2B-modules geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Maak een bedrijfsaccount.
1. Gebruik het eindpunt `/V1&#x200B;/company&#x200B;/<company_id>` . Om het gecreeerde bedrijf bij te werken, zie [ het bedrijf ](https://developer.adobe.com/commerce/webapi/rest/b2b/company-object/#update-the-company) in onze ontwikkelaarsdocumentatie bijwerken. Hieronder ziet u een voorbeeld van een lading:

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

<u> Verwachte resultaten </u>:

Er wordt geen e-mail verzonden met de melding &quot;New company registration request&quot; (Nieuwe aanvraag voor bedrijfsregistratie) omdat de API een bestaand bedrijf bijwerkt.

<u> Ware resultaten </u>:

Elke keer dat de API-aanvraag wordt verzonden, wordt een e-mail verzonden met de melding &quot;Nieuwe aanvraag voor bedrijfsregistratie&quot;.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
