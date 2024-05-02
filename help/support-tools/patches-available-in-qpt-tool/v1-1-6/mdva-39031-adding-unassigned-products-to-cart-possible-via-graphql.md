---
title: "MDVA-39031: Toevoegen van niet-toegewezen producten aan het karretje mogelijk via GraphQL"
description: De MDVA-39031-patch lost het probleem op dat het via GraphQL toevoegen van een product aan het winkelwagentje mogelijk is, zelfs als het niet aan de doelwebsite is toegewezen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 is geïnstalleerd. De patch-id is MDVA-39031. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 5bbd64d1-06ae-4cab-a20e-0e5e5807742b
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-39031: Toevoegen van niet-toegewezen producten aan het karretje via GraphQL

De MDVA-39031-patch lost het probleem op dat het via GraphQL toevoegen van een product aan het winkelwagentje mogelijk is, zelfs als het niet aan de doelwebsite is toegewezen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 is geïnstalleerd. De patch-id is MDVA-39031. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een product via GraphQL aan het winkelwagentje toevoegen is mogelijk, zelfs als het niet aan de doelwebsite is toegewezen.

<u>Stappen om te reproduceren</u>:

1. Maak een secundaire website.
1. Maak een product en wijs het toe aan de primaire website.
1. Met GraphQL maakt u een leeg winkelwagentje voor de secundaire website.

   <pre>
    <code class="language-graphql">
    mutation{
     createEmptyCart
    }
    </code>
    </pre>

   Met kopteksten zoals:

   <pre>
    <code class="language-graphql">
    {
      "Store":"en_au"
    }
    </code>
    </pre>

1. Voeg het product dat is toegewezen aan de primaire website toe aan de wagen op de secundaire website.

   <pre>
    <code class="language-graphql">
    mutation {
      addProductsToCart(
          cartId: "XHrUN2nJ37OqDByhtL0VC8OxYsEZs41c"
          cartItems: [
            {
              quantity: 1
              sku: "p1"
            }
          ]
        ) {
          cart {
           items {
            product {
              name
              sku
            }
            quantity
          }
        }
      }
    }
    </code>
    </pre>

   Kopteksten

   <pre>
    <code class="language-graphql">
    {
      "Store":"en_au"
    }
    </code>
    </pre>

<u>Verwachte resultaten</u>:

Het product wordt niet aan het winkelwagentje toegevoegd omdat het niet is toegewezen aan de winkel die in de koptekst is gedefinieerd.

<u>Werkelijke resultaten</u>:

Het product wordt met succes aan het karretje toegevoegd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
