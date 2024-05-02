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

# Kan niet opslaan *contact* als URL-sleutel

Dit artikel biedt een oplossing voor het probleem wanneer u het niet kunt opslaan *contact* als een URL-sleutel (bijvoorbeeld &quot;/contact&quot;) voor producten of CMS-pagina&#39;s.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.4.x

## Probleem

U kunt een product of CMS-pagina niet opslaan met de term *contact* als URL-sleutel. Wanneer u de URL-sleutel probeert op te slaan, ontvangt u een fout die aangeeft dat de URL-sleutel een dubbele URL is.

<u>Stappen om te reproduceren</u>:

Een CMS-pagina maken met *contact* als URL-sleutel.

<u>Verwacht resultaat</u>:

De pagina wordt opgeslagen met *contact* als URL-sleutel.

<u>Werkelijk resultaat</u>:

U kunt de pagina niet opslaan. De fout wordt weergegeven: *Met de waarde die u opgeeft in het veld URL-sleutel, wordt een bestaande URL gegenereerd.*

## Oorzaak

*Contact* is een gereserveerd woord dat is gedefinieerd in `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## Oplossing

U kunt de term niet gebruiken *contact* als URL-sleutel kunt u echter de term *contact* gecombineerd met een andere letter of een ander getal (bijvoorbeeld *contact1* en *contact2*). Hoewel de term niet hoeft te worden gebruikt *contact+\&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;>* kan de term een willekeurige tekenreeks zijn, zolang de lengte niet meer dan 255 tekens bedraagt.

Voer de volgende stappen uit:

1. Meld u aan bij Commerce Admin.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Klik op **[!UICONTROL Add URL Rewrite]**.
1. Selecteren *[!UICONTROL Custom]* op de [!UICONTROL Create URL Rewrite] vervolgkeuzelijst.
   1. In de [!UICONTROL Request Path], typt u &quot;contact&quot;. Let erop dat de [!UICONTROL Request Path] is wat een gebruiker in browser en [!UICONTROL Target Path] is waar het moet worden omgeleid naar.
   1. In de [!UICONTROL Target Path]Typ de nieuwe URL-sleutel (bijvoorbeeld &quot;contact1&quot;).
   1. Selecteren *[!UICONTROL No]* in de [!UICONTROL Redirect] vervolgkeuzelijst.

## Gerelateerde lezing

* [URL herschrijft](https://docs.magento.com/user-guide/marketing/url-rewrite.html) in onze gebruikershandleiding.
* [SEO Best practices](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) in onze gebruikershandleiding.
