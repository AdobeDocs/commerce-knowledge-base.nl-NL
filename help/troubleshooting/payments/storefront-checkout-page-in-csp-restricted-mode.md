---
title: Afhandelingspagina voor storefront oplossen in [!UICONTROL CSP] beperkte modus
description: In dit artikel worden de fouten uitgelegd die u kunt ervaren bij het weergeven van de afhandelingspagina in de modus CSP-beperkt en worden oplossingen geboden voor het verhelpen van deze fouten.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Afhandelingspagina voor storefront oplossen in [!UICONTROL CSP] beperkte modus

Dit artikel bevat uitleg en oplossingen voor Adobe Commerce 2.4.7-problemen tijdens het bekijken van de pagina voor afrekenen in **[!UICONTROL CSP restricted mode]**, met de &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;- foutbericht in het logboek van de browserconsole.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur, Adobe Commerce op locatie en Magento Open Source:

* 2.4.7.
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Probleem - Afhandelingspagina voor winkelobject is verbroken of kan niet worden geladen

De **winkeluitchecken** pagina is verbroken of kan niet worden geladen, met &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;- foutbericht in het logboek van de browserconsole.

<u>Stappen om te reproduceren</u>:

1. Ga naar de winkel.
1. Voeg een product toe aan het winkelwagentje en ga verder met het afrekenen.

<u>Verwachte resultaten</u>:

De uitcheckpagina wordt normaal volledig geladen.

<u>Werkelijke resultaten</u>:

De uitcheckpagina is leeg of bevat ontbrekende componenten. Het volgende [!DNL JS] de fout wordt getoond in het browser consolelogboek: &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger: **[!UICONTROL CSP]** is geconfigureerd in `restrict-mode`standaard, voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in `report-only` voor alle andere pagina&#39;s.
De overeenkomstige **[!UICONTROL CSP]** header bevat niet de `unsafe-inline` trefwoord in de `script-src` richtlijn voor betalingspagina&#39;s. Alleen [!DNL whitelisted] inline scripts zijn toegestaan.

### Oplossing

Gebruikers kunnen browserfouten zien als gevolg van bepaalde scripts die zijn geblokkeerd vanwege **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Als u dit probleem wilt verhelpen, moet u</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de geblokkeerde scripts gebruiken `SecureHtmlRenderer` klasse.
1. Gebruik de `CSPNonceProvider` klasse om toe te staan dat scripts worden uitgevoerd.
Adobe Commerce en Magento Open Source 2.4.7 en hoger bevatten een **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] om het genereren van unieke [!DNL nonce] tekenreeksen voor elke aanvraag. Deze [!DNL nonce] tekenreeksen worden vervolgens gekoppeld aan de [!UICONTROL CSP] header.

   Gebruik de `generateNonce` functie in `Magento\Csp\Helper\CspNonceProvider` om een [!DNL nonce] tekenreeks.

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

1. [Voeg een [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) naar de module `csp_whitelist.xml` bestand.

## Uitgave - Betalingsmethode ontbreekt of werkt niet

De betalingsmethode ontbreekt of werkt niet aan de **winkeluitchecken** pagina, met de &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;- foutbericht in het logboek van de browserconsole.

<u>Stappen om te reproduceren</u>:

1. Ga naar de winkel.
2. Voeg een product toe aan het winkelwagentje en ga verder met het afrekenen.
3. Selecteer een betalingsmethode.

<u>Verwachte resultaten</u>:

U kunt een betalingsmethode selecteren en doorgaan met het plaatsen van een bestelling.

<u>Werkelijke resultaten</u>:

De betalingsmethode ontbreekt of werkt niet. Het volgende [!DNL JS] de fout wordt getoond in het browser consolelogboek: &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger: **[!UICONTROL CSP]** is geconfigureerd in `restrict-mode`standaard, voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in `report-only` voor alle andere pagina&#39;s.
De overeenkomstige **[!UICONTROL CSP]** header bevat niet de `unsafe-inline` trefwoord in de `script-src` richtlijn voor betalingspagina&#39;s. Alleen [!DNL whitelisted] inline scripts zijn toegestaan.

### Oplossing

Gebruikers kunnen browserfouten zien als gevolg van bepaalde scripts die zijn geblokkeerd vanwege **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Als u dit probleem wilt verhelpen, moet u</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de geblokkeerde scripts gebruiken `SecureHtmlRenderer` klasse.
1. Gebruik de `CSPNonceProvider` klasse om toe te staan dat scripts worden uitgevoerd.
Adobe Commerce en Magento Open Source 2.4.7 en hoger bevatten een **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] om het genereren van unieke [!DNL nonce] tekenreeksen voor elke aanvraag. Deze [!DNL nonce] tekenreeksen worden vervolgens gekoppeld aan de [!UICONTROL CSP] header.

   Gebruik de `generateNonce` functie in `Magento\Csp\Helper\CspNonceProvider` om een [!DNL nonce] tekenreeks.

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

1. [Voeg een [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) naar de module `csp_whitelist.xml` bestand.

## Probleem - Klant kan geen bestelling plaatsen

Een klant kan een bestelling niet plaatsen met &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;- foutbericht in het logboek van de browserconsole.

<u>Stappen om te reproduceren</u>:

1. Ga naar de winkel.
2. Voeg een product toe aan het winkelwagentje en ga verder met het afrekenen.
3. Selecteer een betalingsmethode.
4. Klikken **Opdracht plaatsen**.

<u>Verwachte resultaten</u>:

U kunt een bestelling plaatsen.

<u>Werkelijke resultaten</u>:

U kunt geen bestelling plaatsen. Het volgende [!DNL JS] de fout wordt getoond in het browser consolelogboek: &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger: **[!UICONTROL CSP]** is geconfigureerd in `restrict-mode`standaard, voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in `report-only` voor alle andere pagina&#39;s.
De overeenkomstige **[!UICONTROL CSP]** header bevat niet de `unsafe-inline` trefwoord in de `script-src` richtlijn voor betalingspagina&#39;s. Alleen [!DNL whitelisted] inline scripts zijn toegestaan.

### Oplossing

Gebruikers kunnen browserfouten zien als gevolg van bepaalde scripts die zijn geblokkeerd vanwege **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Als u dit probleem wilt verhelpen, moet u</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) de geblokkeerde scripts gebruiken `SecureHtmlRenderer` klasse.
1. Gebruik de `CSPNonceProvider` klasse om toe te staan dat scripts worden uitgevoerd.
Adobe Commerce en Magento Open Source 2.4.7 en hoger bevatten een **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] om het genereren van unieke [!DNL nonce] tekenreeksen voor elke aanvraag. Deze [!DNL nonce] tekenreeksen worden vervolgens gekoppeld aan de [!UICONTROL CSP] header.

   Gebruik de `generateNonce` functie in `Magento\Csp\Helper\CspNonceProvider` om een [!DNL nonce] tekenreeks.

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

1. [Voeg een [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) naar de module `csp_whitelist.xml` bestand.
