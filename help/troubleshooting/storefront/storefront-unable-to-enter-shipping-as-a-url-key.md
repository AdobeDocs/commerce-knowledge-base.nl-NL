---
title: Kan verzending niet opslaan als URL-sleutel
description: Dit artikel biedt een oplossing voor het probleem wanneer u "Verzending" niet kunt opslaan als een URL-sleutel (bijvoorbeeld "/verzending") voor producten of CMS-pagina's. Wanneer u de URL-sleutel probeert op te slaan, ontvangt u een fout die aangeeft dat de URL-sleutel een dubbele URL is.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Kan verzending niet opslaan als URL-sleutel

Dit artikel biedt een oplossing voor het probleem wanneer u &quot;Verzending&quot; niet kunt opslaan als een URL-sleutel (bijvoorbeeld &quot;/verzending&quot;) voor producten of CMS-pagina&#39;s. Wanneer u de URL-sleutel probeert op te slaan, ontvangt u een fout die aangeeft dat de URL-sleutel een dubbele URL is.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.4.x

## Probleem

U kunt een CMS-pagina met de term &quot;verzending&quot; in de URL-sleutel niet opslaan.

<u>Stappen om te reproduceren</u>:

Maak een CMS-pagina met de URL-sleutel als &quot;verzending&quot;.

<u>Verwacht resultaat</u>:

De pagina wordt met &quot;Verzending&quot; opgeslagen in de URL-sleutel.

<u>Werkelijk resultaat</u>:

U kunt het bestand niet opslaan en er wordt een fout weergegeven: *Met de waarde die u opgeeft in het veld URL-sleutel, wordt een bestaande URL gegenereerd.*

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

Je kunt de term &#39;verzending&#39; niet gebruiken in je URL-sleutel. Je kunt echter de term &#39;verzending&#39; gebruiken in combinatie met een andere letter of een ander nummer (bijvoorbeeld &#39;verzending1&#39; en &#39;verzending2&#39;). Hoewel de term niet &quot;verzending&quot; hoeft te zijn+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - de term kan een willekeurige tekenreeks zijn, zolang de lengte niet meer dan 255 tekens bedraagt.

Voer de volgende stappen uit:

1. Meld u aan bij de Commerce-beheerder.
1. Ga naar **Marketing** > SEO &amp; Search > **URL herschrijft**.
1. Klikken **URL-herschrijven toevoegen**.
1. Selecteren *Aangepast* op Create URL herschrijft drop-down.
   1. Typ in het aanvraagpad &quot;verzending&quot;. Opmerking: het aanvraagpad is het pad dat een gebruiker in de browser invoert en het doelpad is het pad waarnaar de gebruiker moet omleiden.
   1. Typ in het doelpad de nieuwe URL-sleutel (bijvoorbeeld &quot;Shipping1&quot;).
   1. Selecteren **Nee** in de vervolgkeuzelijst Omleiden.

## Gerelateerde lezing

* [URL herschrijft](https://docs.magento.com/user-guide/marketing/url-rewrite.html) in onze gebruikershandleiding.
* [SEO Best practices](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) in onze gebruikershandleiding.
