---
title: '''MDVA-41631: Fout bij het ophalen van bestelgegevens zonder optionele waarde ''phone'''
description: De MDVA-41631-patch verhelpt het probleem waarbij gebruikers een fout krijgen bij het ophalen van bestellingsgegevens zonder optionele "telefoon"-waarde via GraphQL. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631: Fout bij het ophalen van bestelgegevens zonder optionele waarde &quot;phone&quot;

De MDVA-41631-patch verhelpt het probleem waarbij gebruikers een fout krijgen bij het ophalen van bestellingsgegevens zonder optionele &quot;telefoon&quot;-waarde via GraphQL. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers krijgen via GraphQL een fout bij het ophalen van bestelgegevens zonder optionele waarde voor &quot;Telefoon&quot;.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkel** > **Configuratie** > **Klanten** > **Klantconfiguratie** > **Naam- en adresopties** > **Telefoon tonen** en stel het telefoonnummer in als optioneel.
1. Plaats een bestelling met GraphQL API als aangemelde klant.
   * Stel het telefoonnummer niet in bij het instellen van het factuuradres en het verzendadres. Volg de instructies op in [Zelfstudie over GraphQL Checkout](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-customer.html) in onze ontwikkelaarsdocumentatie.
1. De bestelling ophalen met de GraphQL [customerOrders-query](https://devdocs.magento.com/guides/v2.4/graphql/queries/customer-orders.html).

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>Verwachte resultaten</u>:

Gebruikers krijgen bestelgegevens.

<u>Werkelijke resultaten</u>:

Gebruikers krijgen de volgende fout: *&quot;message&quot;: &quot;Internal server error&quot;,*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
