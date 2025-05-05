---
title: 'MDVA-37748: De vraag van GraphQL keert producten terug die niet aan gedeelde catalogus worden toegewezen'
description: De patch MDVA-37748 verhelpt het probleem waarbij een GraphQL-query producten retourneert die niet zijn toegewezen aan een gedeelde catalogus. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 is geïnstalleerd. De patch-id is MDVA-37748. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 1f441882-dc14-433c-aa03-ff22483ce5a7
feature: B2B, GraphQL, Catalog Management, Categories, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# MDVA-37748: De vraag van GraphQL keert producten terug die niet aan gedeelde catalogus worden toegewezen

De patch MDVA-37748 verhelpt het probleem waarbij een GraphQL-query producten retourneert die niet zijn toegewezen aan een gedeelde catalogus. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 geïnstalleerd is. De patch-id is MDVA-37748. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL-query retourneert producten die niet aan een gedeelde catalogus zijn toegewezen.

<u> Eerste vereisten </u>:

B2B-modules worden geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Maak twee producten en wijs deze toe aan een categorie:
   * Product 1 - Openbaar
   * Product 2

1. Wijs &#39;Product 1 - Openbaar&#39; toe aan de gedeelde standaardcatalogus (Algemeen).
1. Maak een extra aangepaste gedeelde catalogus en wijs deze toe aan &quot;Product 2&quot;.
1. Maak een nieuw bedrijf en wijs het toe aan de extra gedeelde catalogus die in stap drie wordt gemaakt.
1. Na de uitvoering/redex van de kroon, op het front, bevestig dat u &quot;Product 1 - Openbaar&quot;kunt zien als u niet het programma wordt geopend.
1. Meld u aan als beheerder van het bedrijf dat u in stap 4 hebt gemaakt en bevestig dat u alleen &quot;Product 2&quot; ziet.
1. Vraag een machtigingstoken aan met behulp van de volgende GraphQL-query:

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(
        email: "company.admin@exapmle.test"
        password: "password"
      ) &lbrace;
        token
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Voeg kopbal **waarde-van-het-teken van de Toestemming** toe en voer de volgende vraag van GraphQL uit:

   <pre>
    <code class="language-graphql">
    &lbrace;
      products(
          filter: {},
          pageSize: 100,
          currentPage: 1
          sort: {}
        ) &lbrace;
          total_count
          page_info &lbrace;
            page_size
            current_page
          &rbrace;
          aggregations &lbrace;
            attribute_code
            count
            label
            options &lbrace;
              label
              value
              count
            &rbrace;
          &rbrace;
          items &lbrace;
            name
            sku
            created_at
            updated_at
            stock_status
            description {html}
            short_description {html}
            url_key
            url_path
            price_tiers&lbrace;
              final_price&lbrace;
                  value
                  currency
                &rbrace;
              discount&lbrace;
                  amount_off
                  percent_off
                &rbrace;
              quantity
            &rbrace;
            price_range &lbrace;
             maximum_price &lbrace;
              regular_price &lbrace;
                value
              &rbrace;
              final_price &lbrace;
                value
              &rbrace;
            &rbrace;
            minimum_price &lbrace;
              regular_price &lbrace;
                value
              &rbrace;
              final_price &lbrace;
               value
              &rbrace;
            &rbrace;
          &rbrace;
          image &lbrace;
           url
          &rbrace;
          thumbnail &lbrace;
           url
          &rbrace;
          small_image &lbrace;
           url
          &rbrace;
          media_gallery &lbrace;
           url
          &rbrace;
          ... on ConfigurableProduct &lbrace;
            configurable_options &lbrace;
             id

             label
             position
             use_default
             attribute_code
             values &lbrace;
               value_index
               label
               swatch_data &lbrace;
                 value
               &rbrace;
            &rbrace;
            product_id
          &rbrace;
          variants &lbrace;
            product &lbrace;
              id
              name
              sku
              &#x200B;#margin
              &#x200B;#margin_percentage
              image &lbrace;
                url
              &rbrace;
              small_image &lbrace;
                url
              &rbrace;
              thumbnail &lbrace;
                url
              &rbrace;
              media_gallery&lbrace;
                url
              &rbrace;
              attribute_set_id
              ... on PhysicalProductInterface &lbrace;
                weight
              &rbrace;
              price_range &lbrace;
                minimum_price &lbrace;
                  regular_price &lbrace;
                    value
                    currency
                  &rbrace;
                &rbrace;
              &rbrace;
            &rbrace;
            attributes &lbrace;
              label
              code
              value_index
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;

    &rbrace;
&rbrace;
</code>
</pre>

<u> Verwachte resultaten </u>:

De telling en het product die door GraphQL zijn geretourneerd, houden alleen rekening met het product dat is toegewezen aan de gedeelde catalogus die is gekoppeld aan de aangemelde gebruiker.

<u> Ware resultaten </u>:

Alleen &quot;Product 2&quot; wordt geretourneerd, maar `total_count` geeft er twee weer.

<pre>
<code class="language-graphql">
&lbrace;
  "data": &lbrace;
    "products": &lbrace;
      "total_count": 2,
      "page_info": &lbrace;
        "page_size": 100,
        "current_page": 1
      &rbrace;,
      "aggregations": &lbrack;
        &lbrace;
          "attribute_code": "price",
          "count": 2,
          "label": "Price",
          "options": &lbrack;
            &lbrace;
              "label": "0-100",
              "value": "0_100",
              "count": 1
            &rbrace;,
            &lbrace;
              "label": "100-200",
              "value": "100_200",
              "count": 1
            &rbrace;
          &rbrack;
        &rbrace;,
        &lbrace;
          "attribute_code": "category_id",
          "count": 1,
          "label": "Category",
          "options": &lbrack;
            &lbrace;
              "label": "Cat 1",
              "value": "3",
              "count": 2
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrack;,
      "items": &lbrack;
        &lbrace;
          "name": "Product 2",
          "sku": "Product 2",
          "created_at": "2021-05-12 10:51:44",
          "updated_at": "2021-05-12 11:03:24",
          "stock_status": "IN_STOCK",
          "description": &lbrace;
            "html": ""
          &rbrace;,
          "short_description": &lbrace;
            "html": ""
          &rbrace;,
          "url_key": "product-2",
          "url_path": null,
          "price_tiers": &lbrack;
            &lbrace;
              "final_price": &lbrace;
                "value": 90,
                "currency": "USD"
              &rbrace;,
              "discount": &lbrace;
                "amount_off": 10,
                "percent_off": 10
              &rbrace;,
              "quantity": 1
            &rbrace;
          &rbrack;,
          "price_range": &lbrace;
            "maximum_price": &lbrace;
              "regular_price": &lbrace;
                "value": 100
              &rbrace;,
              "final_price": &lbrace;
                "value": 90
              &rbrace;
            &rbrace;,
            "minimum_price": &lbrace;
              "regular_price": &lbrace;
                "value": 100
              &rbrace;,
              "final_price": &lbrace;
                "value": 90
              &rbrace;
            &rbrace;
          &rbrace;,
          "image": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/image.jpg"
          &rbrace;,
          "thumbnail": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/thumbnail.jpg"
          &rbrace;,
          "small_image": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/small_image.jpg"
          &rbrace;,
          "media_gallery": []
        &rbrace;
      &rbrack;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
