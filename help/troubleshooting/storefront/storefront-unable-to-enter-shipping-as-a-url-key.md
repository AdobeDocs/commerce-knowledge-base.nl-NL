---
title: Kan verzending niet opslaan als URL-sleutel
description: Dit artikel biedt een oplossing voor het probleem wanneer u verzending niet kunt opslaan als een URL-sleutel (_bijv. /Shipping_) voor producten of CMS-pagina's. Wanneer u de URL-sleutel probeert op te slaan, ontvangt u een fout die aangeeft dat de URL-sleutel een dubbele URL is.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 1ce963142a261a17e2b42f79dd567c8484ec5b3e
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Kan niet opslaan _verzending_ als URL-sleutel

Dit artikel biedt een oplossing voor het probleem wanneer u de verzending niet als URL-sleutel kunt opslaan (_bijv., /Shipping_) voor producten of CMS-pagina&#39;s. Wanneer u de URL-sleutel probeert op te slaan, ontvangt u een fout die aangeeft dat de URL-sleutel een dubbele URL is.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.4.x

## Probleem

U kunt een CMS-pagina met de term niet opslaan _verzending_ in de URL-sleutel.

<u>Stappen om te reproduceren</u>:

Een **[!UICONTROL CMS page]** met de URL-sleutel als _verzending_.

<u>Verwacht resultaat</u>:

De pagina wordt opgeslagen met _verzending_ als URL-sleutel.

<u>Werkelijk resultaat</u>:

U kunt niet opslaan omdat deze fout optreedt:
*Met de waarde die u opgeeft in het veld URL-sleutel, wordt een bestaande URL gegenereerd.*

## Oorzaak

Verzending is een gereserveerd woord dat is gedefinieerd in `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## Oplossing

U kunt de term niet gebruiken _verzending_ in uw URL-sleutel - maar u kunt de term _verzending_ gecombineerd met een andere letter of een ander getal (_Bijvoorbeeld verzending1 en verzending2_).

Hoewel de term niet hoeft te worden gebruikt _verzending_+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - de term kan een willekeurige tekenreeks zijn zolang de lengte niet wordt overschreden *255* tekens.

## Voer de volgende stappen uit:

1. Meld u aan bij de Adobe Commerce-beheerder.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Klik op **[!UICONTROL Add URL Rewrite]**.
1. Selecteren **[!UICONTROL Custom]** in de **[!UICONTROL Create URL Rewrite]** vervolgkeuzelijst.
   1. Typ de [!UICONTROL Request Path] als **_verzending_**.
   1. In de **[!UICONTROL Target Path]** Typ de nieuwe URL-sleutel (_Bijvoorbeeld &quot;Shipping1&quot;_).
   1. Selecteren **[!UICONTROL No]** in de **[!UICONTROL Redirect]** vervolgkeuzelijst.


      (**Opmerking**: Het verzoekpad is het pad dat een gebruiker in de browser invoert en het doelpad is het pad waarnaar de gebruiker moet omleiden.)

Vermijd bovendien het gebruik van deze trefwoorden met het label *gereserveerd* trefwoorden die ertoe leiden dat dezelfde uitzondering wordt weergegeven. Als u een van deze trefwoorden gebruikt als een URL-sleutelwaarde, wordt dezelfde fout weergegeven.


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

* [URL herschrijft](https://docs.magento.com/user-guide/marketing/url-rewrite.html) in onze Gebruikershandleiding voor Verkoop en Aanbiedingen.
* [SEO Best practices](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) in onze Gebruikershandleiding voor Merchandising en Promoties..
