---
title: 'MDVA-40830: Winkelkrediet wordt meerdere keren toegepast tijdens bestelling'
description: De patch MDVA-40830 verhelpt het probleem waarbij het winkelkrediet meerdere keren wordt toegepast tijdens de plaatsing van de bestelling. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 is geïnstalleerd. De patch-id is MDVA-40830. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 218a100a-4500-4ef5-bbdb-fbbd12f2fa26
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-40830: Winkelkrediet wordt meerdere keren toegepast tijdens bestelling

De patch MDVA-40830 verhelpt het probleem waarbij het winkelkrediet meerdere keren wordt toegepast tijdens de plaatsing van de bestelling. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 is geïnstalleerd. De patch-id is MDVA-40830. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.7-p2, 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het winkelkrediet wordt meerdere keren toegepast tijdens de plaatsing van de bestelling.

<u>Stappen om te reproduceren</u>:

1. Maak een klant en voeg winkelkrediet toe aan de klantenaccount.
1. Voeg een eenvoudig product toe aan de wagen.
1. Verzendadres en factuuradres voor de winkelwagen instellen.
1. Controleer het grote_totaal van de wagen.
1. Pas superieure creditering op de winkelwagentje toe met behulp van de volgende GraphQL-aanvraag:

<pre>
<code class="language-graphql">
mutation {
  applyStoreCreditToCart(
    input: { cart_id: "%cartId%" }
  ) {
    cart {
      prices {
        grand_total {
          currency
          value
        }
      }
      applied_store_credit {
        applied_balance {
          currency
          value
        }
        current_balance {
          currency
          value
        }
      }
    }
  }
}
</code>
</pre>

<u>Verwachte resultaten</u>:

De waarde van applied_store_credit wordt correct toegepast, en het karttotalen worden correct weerspiegeld in de API reactie.

<u>Werkelijke resultaten</u>:

De waarde van applied_store_credit wordt tweemaal toegepast, die zowel het karretje als het ale_total beïnvloedt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
