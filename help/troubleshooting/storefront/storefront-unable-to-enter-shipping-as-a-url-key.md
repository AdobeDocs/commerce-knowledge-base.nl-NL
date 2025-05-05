---
title: Kan verzending niet opslaan als URL-sleutel
description: Dit artikel biedt een oplossing voor het probleem wanneer u verzending niet kunt opslaan als een URL-sleutel (_bijv. /Shipping_) voor producten of CMS-pagina's. Wanneer u de URL-sleutel probeert op te slaan, ontvangt u een fout die aangeeft dat de URL-sleutel een dubbele URL is.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Kan _het verschepen_ als sleutel URL niet bewaren

Dit artikel verstrekt een tijdelijke oplossing voor de kwestie wanneer u geen het verschepen als sleutel URL (_b.v., /Shipping_) voor producten of de pagina&#39;s van CMS kunt bewaren. Wanneer u de URL-sleutel probeert op te slaan, ontvangt u een fout die aangeeft dat de URL-sleutel een dubbele URL is.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.4.x

## Probleem

U kunt geen pagina van CMS met de termijn _verschepen_ in de sleutel bewaren URL.

<u> Stappen om </u> te reproduceren:

Creeer a **[!UICONTROL CMS page]** met de sleutel URL als _verzendend_.

<u> Verwacht resultaat </u>:

De pagina bewaart met _het verschepen_ als sleutel URL.

<u> Werkelijk resultaat </u>:

U kunt niet opslaan omdat deze fout optreedt:
*de waarde die op het Zeer belangrijke gebied wordt gespecificeerd URL zou een URL produceren die reeds bestaat.*

## Oorzaak

Verzending is een gereserveerd woord dat is gedefinieerd in `vendor/magento/module-shipping/etc/frontend/routes.xml` .

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## Oplossing

U kunt niet de term _verschepen_ in uw sleutel gebruiken URL - nochtans kunt u de termijn _gebruiken die_ met een andere brief of een aantal (_wordt gecombineerd bijvoorbeeld, verschepen1 en verschepen2_).

Hoewel de termijn niet _het verschepen_ + &lt;een ander aantal of brief> moet zijn - de termijn zou om het even welk koord kunnen zijn zolang de lengte *255* karakters niet overschrijdt.

## Voer de volgende stappen uit:

1. Meld u aan bij de Adobe Commerce-beheerder.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]** .
1. Klik op **[!UICONTROL Add URL Rewrite]**.
1. Selecteer **[!UICONTROL Custom]** in de vervolgkeuzelijst **[!UICONTROL Create URL Rewrite]** .
   1. Typ [!UICONTROL Request Path] als **_verschepen_**.
   1. In **[!UICONTROL Target Path]**, typ de nieuwe sleutel URL (_Bijvoorbeeld, &quot;Shipping1&quot;_).
   1. Selecteer **[!UICONTROL No]** in de vervolgkeuzelijst **[!UICONTROL Redirect]** .


      (**Nota**: De Weg van het Verzoek is wat een gebruiker in browser ingaat en de Weg van het Doel is waar het aan zou moeten opnieuw richten.)

Bovendien vermijd het gebruiken van deze sleutelwoorden die als *gereserveerde* sleutelwoorden worden geëtiketteerd die de zelfde uitzondering veroorzaken om te verschijnen. Als u een van deze trefwoorden gebruikt als een URL-sleutelwaarde, wordt dezelfde fout weergegeven.


```
"admin"
"adminAnalytics"
"analytics"
"api"
"backup"
"bulk"
"captcha"
"catalog"
"catalogsearch"
"checkout"
"cms"
"contact"
"cookie"
"customer"
"directory"
"downloadable"
"giftmessage"
"groupedProduct"
"indexer"
"instantpurchase"
"loginascustomer"
"marketplace"
"mui"
"multishipping"
"newsletter"
"oauth"
"paypal"
"persistent"
"productalert"
"releaseNotification"
"reports"
"review"
"robots"
"rss"
"sales"
"search"
"security"
"sendfriend"
"shipping"
"stores"
"swagger"
"swatches"
"tax"
"theme"
"translation"
"vault"
"wishlist"
```

## Gerelateerde lezing

* [ URL herschrijft ](https://experienceleague.adobe.com/nl/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite) in onze Gids van de Gebruiker van Merchandising en van Bevorderingen.
* {de Beste praktijken van 0} SEO [&#128279;](https://experienceleague.adobe.com/nl/docs/commerce-admin/marketing/seo/seo-overview) in onze Gids van de Gebruiker van Merchandising en van Bevorderingen.
