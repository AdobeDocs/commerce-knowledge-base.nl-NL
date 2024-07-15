---
title: Kan *contact* niet opslaan als URL-sleutel
description: Dit artikel biedt een oplossing voor het probleem als u *contact* niet kunt opslaan als een URL-sleutel (bijvoorbeeld "/contact") voor producten of CMS-pagina's. Wanneer u de URL-sleutel probeert op te slaan, ontvangt u een fout die aangeeft dat de URL-sleutel een dubbele URL is.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Kan *contact* niet opslaan als sleutel URL

Dit artikel verstrekt een tijdelijke oplossing voor de kwestie wanneer u *contact* niet als sleutel URL (b.v., &quot;/contact&quot;) voor producten of CMS pagina&#39;s kunt bewaren.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.4.x

## Probleem

U kunt geen product of een pagina opslaan CMS gebruikend de termijn *contact* als sleutel URL. Wanneer u de URL-sleutel probeert op te slaan, ontvangt u een fout die aangeeft dat de URL-sleutel een dubbele URL is.

<u> Stappen om </u> te reproduceren:

Creeer een CMS pagina met *contact* als sleutel URL.

<u> Verwacht resultaat </u>:

De pagina wordt bewaard met *contact* als sleutel URL.

<u> Werkelijk resultaat </u>:

U kunt de pagina niet opslaan. U krijgt de fout: *de waarde die op het Zeer belangrijke gebied wordt gespecificeerd URL zou een URL produceren die reeds bestaat.*

## Oorzaak

*Contact* is een gereserveerd woord dat in `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml` wordt bepaald.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## Oplossing

U kunt niet het term *contact* als uw sleutel gebruiken URL, echter, kunt u het term *contact* gebruiken gecombineerd met een andere brief of een aantal (bijvoorbeeld, *contact1* en *contact2*). Hoewel de termijn niet *contact+ \ &lt;een ander aantal of brief \>* moet zijn, zou de termijn om het even welk koord kunnen zijn zolang de lengte niet 255 karakters overschrijdt.

Voer de volgende stappen uit:

1. Meld u aan bij Commerce Admin.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]** .
1. Klik op **[!UICONTROL Add URL Rewrite]**.
1. Selecteer *[!UICONTROL Custom]* in de vervolgkeuzelijst [!UICONTROL Create URL Rewrite] .
   1. Typ in [!UICONTROL Request Path] &quot;contact&quot;. De instructie [!UICONTROL Request Path] is de instructie die een gebruiker in de browser invoert en de instructie [!UICONTROL Target Path] is de locatie waarnaar de gebruiker moet omleiden.
   1. Typ in de [!UICONTROL Target Path] de nieuwe URL-sleutel (bijvoorbeeld &quot;contact1&quot;).
   1. Selecteer *[!UICONTROL No]* in de vervolgkeuzelijst [!UICONTROL Redirect] .

## Gerelateerde lezing

* [ URL herschrijft ](https://docs.magento.com/user-guide/marketing/url-rewrite.html) in onze gebruikersgids.
* [ SEO Beste praktijken ](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) in onze gebruikersgids.
