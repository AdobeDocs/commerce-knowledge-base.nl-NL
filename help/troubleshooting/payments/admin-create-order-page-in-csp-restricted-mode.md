---
title: Oplossen van problemen bij het maken van een ordepagina in de beperkte modus van [!UICONTROL CSP]
description: Dit artikel verklaart fouten die tot een orde op Admin leiden wanneer CSP beperkte wijze wordt toegelaten, en verstrekt oplossingen om die fouten te bevestigen.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Oplossen van problemen bij het maken van een ordepagina in de beperkte modus van [!UICONTROL CSP]

Dit artikel verstrekt verklaringen en moeilijke situaties voor Adobe Commerce 2.4.7 kwesties terwijl het creëren van een orde op Admin met **[!UICONTROL CSP restricted mode]** wordt *Toegelaten*, met &quot;*Weigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src...*&quot;foutenmelding in het browser consolelogboek.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur, Adobe Commerce op locatie en Magento Open Source:

* 2.4.7.
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## De kwestie - Admin **creeert orde** pagina is gebroken of kan niet laden

Admin **creeert orde** pagina is gebroken of kan niet laden, met &quot;*dat wordt geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;foutenmelding in het browser consolelogboek.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** .
1. Maak een nieuwe volgorde.

<u> Verwachte resultaten </u>:

Admin **creeert orde** pagina volledig laadt normaal.

<u> Ware resultaten </u>:

Admin **creeert orde** pagina is leeg of ontbrekende componenten. De volgende [!DNL JS] fout wordt getoond in het browser consolelogboek: &quot;*die wordt geweigerd om gealigneerd manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud overtreedt: &quot;manuscript-src...*&quot;

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger is **[!UICONTROL CSP]** standaard geconfigureerd in `restrict-mode` , voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in de `report-only` -modus voor alle andere pagina&#39;s.
De corresponderende header **[!UICONTROL CSP]** bevat niet het trefwoord `unsafe-inline` binnen de aanwijzing `script-src` voor betaalpagina&#39;s. Bovendien zijn alleen [!DNL whitelisted] inlinescripts toegestaan.

### Oplossing

Gebruikers zien mogelijk browserfouten omdat bepaalde scripts zijn geblokkeerd door [!UICONTROL CSP] :

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u> om deze kwestie te bevestigen, moet u één van beide </u>:

1. [[!DNL Whitelist] &#x200B;](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de geblokkeerde manuscripten die de `SecureHtmlRenderer` klasse gebruiken.
1. Gebruik de klasse `CSPNonceProvider` om toe te staan dat scripts worden uitgevoerd.
Adobe Commerce en Magento Open Source 2.4.7 en hoger bevatten een **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] -provider om het genereren van unieke [!DNL nonce] -tekenreeksen voor elke aanvraag te vergemakkelijken. Deze [!DNL nonce] -tekenreeksen worden vervolgens aan de [!UICONTROL CSP] -koptekst gekoppeld.

   Gebruik de functie `generateNonce` in `Magento\Csp\Helper\CspNonceProvider` om een tekenreeks [!DNL nonce] te verkrijgen.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [&#x200B; voeg a  [!DNL hash] &#x200B;](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) aan het dossier van uw module `csp_whitelist.xml` toe.

## Uitgave - Betalingsmethode ontbreekt of werkt niet

De betalingsmethode ontbreekt of werkt niet aan Admin **orde leidt tot pagina**, met &quot;*die wordt geweigerd om gealigneerd manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;foutenmelding in het browser consolelogboek.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** .
1. Maak een nieuwe volgorde.
1. Maak een nieuwe klant.
1. Voer de klantgegevens in.
1. Voer de bestelgegevens in (producten, verzendmethode).
1. Selecteer een betalingsmethode.

<u> Verwachte resultaten </u>:

U kunt een betalingsmethode selecteren en doorgaan met het plaatsen van een bestelling.

<u> Ware resultaten </u>:

De betalingsmethode ontbreekt of werkt niet. De volgende [!DNL JS] fout wordt getoond in het browser consolelogboek: &quot;*die wordt geweigerd om gealigneerd manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud overtreedt: &quot;manuscript-src...*&quot;.

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger is **[!UICONTROL CSP]** standaard geconfigureerd in `restrict-mode` , voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in de `report-only` -modus voor alle andere pagina&#39;s.
De corresponderende header **[!UICONTROL CSP]** bevat niet het trefwoord `unsafe-inline` binnen de aanwijzing `script-src` voor betaalpagina&#39;s. Bovendien zijn alleen [!DNL whitelisted] inlinescripts toegestaan.

### Oplossing

Gebruikers zien mogelijk browserfouten omdat bepaalde scripts zijn geblokkeerd door **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u> om deze kwestie te bevestigen, moet u één van beide </u>:

1. [[!DNL Whitelist] &#x200B;](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de geblokkeerde manuscripten die de `SecureHtmlRenderer` klasse gebruiken.
1. Gebruik de klasse `CSPNonceProvider` om toe te staan dat scripts worden uitgevoerd.
Adobe Commerce en Magento Open Source 2.4.7 en hoger bevatten een **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] -provider om het genereren van unieke [!DNL nonce] -tekenreeksen voor elke aanvraag te vergemakkelijken. Deze [!DNL nonce] -tekenreeksen worden vervolgens aan de [!UICONTROL CSP] -koptekst gekoppeld.

   Gebruik de functie `generateNonce` in `Magento\Csp\Helper\CspNonceProvider` om een tekenreeks [!DNL nonce] te verkrijgen.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [&#x200B; voeg a  [!DNL hash] &#x200B;](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) aan het dossier van uw module `csp_whitelist.xml` toe.

## Probleem - Admin kan geen bestelling plaatsen

Admin kan geen orde op Admin **voorleggen leidt tot ordepagina**, met &quot;*die wordt geweigerd om gealigneerd manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;foutenmelding in het browser consolelogboek.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** .
1. Maak een nieuwe volgorde.
1. Maak een nieuwe klant.
1. Voer de klantgegevens in.
1. Voer de bestelgegevens in (producten, verzendmethode).
1. Selecteer een betalingsmethode.
1. Verzend de bestelling.

<u> Verwachte resultaten </u>:

U kunt een bestelling verzenden.

<u> Ware resultaten </u>:

U kunt geen bestelling verzenden. De volgende [!DNL JS] fout wordt getoond in het browser consolelogboek: &quot;*die wordt geweigerd om gealigneerd manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud overtreedt: &quot;manuscript-src...*&quot;

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger is **[!UICONTROL CSP]** standaard geconfigureerd in `restrict-mode` , voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in de `report-only` -modus voor alle andere pagina&#39;s.
De corresponderende header **[!UICONTROL CSP]** bevat niet het trefwoord `unsafe-inline` binnen de aanwijzing `script-src` voor betaalpagina&#39;s. Bovendien zijn alleen [!DNL whitelisted] inlinescripts toegestaan.

### Oplossing

Gebruikers zien mogelijk browserfouten omdat bepaalde scripts zijn geblokkeerd door **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u> om deze kwestie te bevestigen, moet u één van beide </u>:

1. [[!DNL Whitelist] &#x200B;](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de geblokkeerde manuscripten die de `SecureHtmlRenderer` klasse gebruiken.
1. Gebruik de klasse `CSPNonceProvider` om toe te staan dat scripts worden uitgevoerd.
Adobe Commerce en Magento Open Source 2.4.7 en hoger bevatten een **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] -provider om het genereren van unieke [!DNL nonce] -tekenreeksen voor elke aanvraag te vergemakkelijken. Deze [!DNL nonce] -tekenreeksen worden vervolgens aan de [!UICONTROL CSP] -koptekst gekoppeld.

   Gebruik de functie `generateNonce` in `Magento\Csp\Helper\CspNonceProvider` om een tekenreeks [!DNL nonce] te verkrijgen.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [&#x200B; voeg a  [!DNL hash] &#x200B;](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) aan het dossier van uw module `csp_whitelist.xml` toe.
