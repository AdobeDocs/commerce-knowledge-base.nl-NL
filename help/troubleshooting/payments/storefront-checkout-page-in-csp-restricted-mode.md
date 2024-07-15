---
title: Probleem met uitchecken van storefront oplossen in de beperkte modus van [!UICONTROL CSP]
description: In dit artikel worden de fouten uitgelegd die u kunt ervaren bij het weergeven van de afhandelingspagina in de modus CSP-beperkt en worden oplossingen geboden voor het verhelpen van deze fouten.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Probleem met uitchecken van storefront oplossen in de beperkte modus van [!UICONTROL CSP]

Dit artikel verstrekt verklaringen en moeilijke situaties voor Adobe Commerce 2.4.7 kwesties terwijl het bekijken van de controlepagina in **[!UICONTROL CSP restricted mode]**, met &quot;*die wordt geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud overtreedt: &quot;manuscript-src...*&quot;foutenmelding in het browser consolelogboek.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur, Adobe Commerce op locatie en Magento Open Source:

* 2.4.7.
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Probleem - Afhandelingspagina voor winkelobject is verbroken of kan niet worden geladen

De **storefront controle** pagina is gebroken of kan niet laden, met &quot;*die wordt geweigerd om gealigneerd manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;foutenmelding in het browser consolelogboek.

<u> Stappen om </u> te reproduceren:

1. Ga naar de winkel.
1. Voeg een product toe aan het winkelwagentje en ga verder met het afrekenen.

<u> Verwachte resultaten </u>:

De uitcheckpagina wordt normaal volledig geladen.

<u> Ware resultaten </u>:

De uitcheckpagina is leeg of bevat ontbrekende componenten. De volgende [!DNL JS] fout wordt getoond in het browser consolelogboek: &quot;*die wordt geweigerd om gealigneerd manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud overtreedt: &quot;manuscript-src...*&quot;

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger is **[!UICONTROL CSP]** standaard geconfigureerd in `restrict-mode` , voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in de `report-only` -modus voor alle andere pagina&#39;s.
De corresponderende header **[!UICONTROL CSP]** bevat niet het trefwoord `unsafe-inline` binnen de aanwijzing `script-src` voor betaalpagina&#39;s. Bovendien zijn alleen [!DNL whitelisted] inlinescripts toegestaan.

### Oplossing

Gebruikers zien mogelijk browserfouten omdat bepaalde scripts zijn geblokkeerd door **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u> om deze kwestie te bevestigen, moet u één van beide </u>:

1. [[!DNL Whitelist] ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de geblokkeerde manuscripten die de `SecureHtmlRenderer` klasse gebruiken.
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

1. [ voeg a  [!DNL hash] ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) aan het dossier van uw module `csp_whitelist.xml` toe.

## Uitgave - Betalingsmethode ontbreekt of werkt niet

De betalingsmethode ontbreekt of werkt niet aan de **storefront controle** pagina, met &quot;*die wordt geweigerd om gealigneerd manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;foutenmelding in het browser consolelogboek.

<u> Stappen om </u> te reproduceren:

1. Ga naar de winkel.
2. Voeg een product toe aan het winkelwagentje en ga verder met het afrekenen.
3. Selecteer een betalingsmethode.

<u> Verwachte resultaten </u>:

U kunt een betalingsmethode selecteren en doorgaan met het plaatsen van een bestelling.

<u> Ware resultaten </u>:

De betalingsmethode ontbreekt of werkt niet. De volgende [!DNL JS] fout wordt getoond in het browser consolelogboek: &quot;*die wordt geweigerd om gealigneerd manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud overtreedt: &quot;manuscript-src...*&quot;

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger is **[!UICONTROL CSP]** standaard geconfigureerd in `restrict-mode` , voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in de `report-only` -modus voor alle andere pagina&#39;s.
De corresponderende header **[!UICONTROL CSP]** bevat niet het trefwoord `unsafe-inline` binnen de aanwijzing `script-src` voor betaalpagina&#39;s. Bovendien zijn alleen [!DNL whitelisted] inlinescripts toegestaan.

### Oplossing

Gebruikers zien mogelijk browserfouten omdat bepaalde scripts zijn geblokkeerd door **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u> om deze kwestie te bevestigen, moet u één van beide </u>:

1. [[!DNL Whitelist] ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de geblokkeerde manuscripten die de `SecureHtmlRenderer` klasse gebruiken.
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

1. [ voeg a  [!DNL hash] ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) aan het dossier van uw module `csp_whitelist.xml` toe.

## Probleem - Klant kan geen bestelling plaatsen

Een klant kan geen orde plaatsen, met &quot;*die wordt geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src...*&quot;foutenmelding in het browser consolelogboek.

<u> Stappen om </u> te reproduceren:

1. Ga naar de winkel.
2. Voeg een product toe aan het winkelwagentje en ga verder met het afrekenen.
3. Selecteer een betalingsmethode.
4. Klik **de Orde van de Plaats**.

<u> Verwachte resultaten </u>:

U kunt een bestelling plaatsen.

<u> Ware resultaten </u>:

U kunt geen bestelling plaatsen. De volgende [!DNL JS] fout wordt getoond in het browser consolelogboek: &quot;*die wordt geweigerd om gealigneerd manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud overtreedt: &quot;manuscript-src...*&quot;

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger is **[!UICONTROL CSP]** standaard geconfigureerd in `restrict-mode` , voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in de `report-only` -modus voor alle andere pagina&#39;s.
De corresponderende header **[!UICONTROL CSP]** bevat niet het trefwoord `unsafe-inline` binnen de aanwijzing `script-src` voor betaalpagina&#39;s. Bovendien zijn alleen [!DNL whitelisted] inlinescripts toegestaan.

### Oplossing

Gebruikers zien mogelijk browserfouten omdat bepaalde scripts zijn geblokkeerd door **[!UICONTROL CSP]** :

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u> om deze kwestie te bevestigen, moet u één van beide </u>:

1. [[!DNL Whitelist] ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de geblokkeerde manuscripten die de `SecureHtmlRenderer` klasse gebruiken.
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

1. [ voeg a  [!DNL hash] ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) aan het dossier van uw module `csp_whitelist.xml` toe.
