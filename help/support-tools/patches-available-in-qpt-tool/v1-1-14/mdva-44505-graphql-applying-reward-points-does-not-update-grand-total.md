---
title: 'MDVA-44505: GraphQL query for cart applying pay-points biedt geen update van het totaal-generaal'
description: Met de MDVA-44505-patch wordt het probleem opgelost dat de GraphQL-query voor een winkelwagen die beloningspunten toepast, geen rekening houdt met de bonuspunten en een onjuist totaal retourneert. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-44505. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 724273ba-b020-4dba-88ae-94968bbd83de
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44505: GraphQL-query voor winkelwagen met bonuspunten werkt het totaal-generaal niet bij

Met de MDVA-44505-patch wordt het probleem opgelost dat de GraphQL-query voor een winkelwagen die beloningspunten toepast, geen rekening houdt met de bonuspunten en een onjuist totaal retourneert. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-44505. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De GraphQL-zoekopdracht voor een winkelwagentje dat bonuspunten toepast, houdt geen rekening met de bonuspunten en retourneert een onjuist totaal-generaal.

<u>Stappen om te reproduceren</u>:

1. Vorm beloningspunten.
1. Maak een winkelwagen en pas wat bonuspunten toe.
1. Roep de `GetCart` query van de `GraphQL` eindpunt en woon uw kar terug:

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. Controleer de algemene totale invoer.
1. Controleer nu het totale aantal winkelwagentjes van de klant met de rest-API (`/rest/V1/carts/mine/totals`).

<u>Verwachte resultaten</u>:

De GraphQL-zoekopdracht voor het winkelwagentje retourneert het juiste totaal, waarbij de bonuspunten in aanmerking worden genomen.

<u>Werkelijke resultaten</u>:

De GraphQL-query houdt geen rekening met de bonuspunten en retourneert een onjuist algemeen totaal.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
