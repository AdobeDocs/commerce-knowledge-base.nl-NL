---
title: Oplossen van problemen bij het maken van een bestelpagina in [!UICONTROL CSP] beperkte modus
description: Dit artikel verklaart fouten die tot een orde op Admin leiden wanneer CSP beperkte wijze wordt toegelaten, en verstrekt oplossingen om die fouten te bevestigen.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Oplossen van problemen bij het maken van een bestelpagina in [!UICONTROL CSP] beperkte modus

Dit artikel bevat uitleg en oplossingen voor de Adobe Commerce 2.4.7-problemen bij het maken van een bestelling op de beheerderszijde met **[!UICONTROL CSP restricted mode]** is *Ingeschakeld*, met de &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;- foutbericht in het logboek van de browserconsole.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur, Adobe Commerce op locatie en Magento Open Source:

* 2.4.7.
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Probleem - beheerder **order maken** pagina is verbroken of kan niet worden geladen

De beheerder **order maken** pagina is verbroken of kan niet worden geladen, met &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;- foutbericht in het logboek van de browserconsole.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Maak een nieuwe volgorde.

<u>Verwachte resultaten</u>:

De beheerder **order maken** pagina wordt normaal volledig geladen.

<u>Werkelijke resultaten</u>:

De beheerder **order maken** pagina is leeg of ontbreken componenten. Het volgende [!DNL JS] de fout wordt getoond in het browser consolelogboek: &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger: **[!UICONTROL CSP]** is geconfigureerd in `restrict-mode`standaard, voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in `report-only` voor alle andere pagina&#39;s.
De overeenkomstige **[!UICONTROL CSP]** header bevat niet de `unsafe-inline` trefwoord in de `script-src` richtlijn voor betalingspagina&#39;s. Alleen [!DNL whitelisted] inline scripts zijn toegestaan.

### Oplossing

Gebruikers kunnen browserfouten zien als gevolg van bepaalde scripts die zijn geblokkeerd vanwege [!UICONTROL CSP]:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

De betalingsmethode ontbreekt of werkt niet op de beheerder **pagina maken**, met de &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;- foutbericht in het logboek van de browserconsole.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Maak een nieuwe volgorde.
1. Maak een nieuwe klant.
1. Voer de klantgegevens in.
1. Voer de bestelgegevens in (producten, verzendmethode).
1. Selecteer een betalingsmethode.

<u>Verwachte resultaten</u>:

U kunt een betalingsmethode selecteren en doorgaan met het plaatsen van een bestelling.

<u>Werkelijke resultaten</u>:

De betalingsmethode ontbreekt of werkt niet. Het volgende [!DNL JS] de fout wordt getoond in het browser consolelogboek: &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;.

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger: **[!UICONTROL CSP]** is geconfigureerd in `restrict-mode`standaard, voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in `report-only` voor alle andere pagina&#39;s.
De overeenkomstige **[!UICONTROL CSP]** header bevat niet de `unsafe-inline` trefwoord in de `script-src` richtlijn voor betalingspagina&#39;s. Alleen [!DNL whitelisted] inline scripts zijn toegestaan.

### Oplossing

Gebruikers kunnen browserfouten zien als gevolg van bepaalde scripts die zijn geblokkeerd vanwege **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

1. [toevoegen [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) naar de module `csp_whitelist.xml` bestand.

## Probleem - Admin kan geen bestelling plaatsen

Een beheerder kan geen bestelling indienen bij de beheerder **orderpagina maken**, met de &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;- foutbericht in het logboek van de browserconsole.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Maak een nieuwe volgorde.
1. Maak een nieuwe klant.
1. Voer de klantgegevens in.
1. Voer de bestelgegevens in (producten, verzendmethode).
1. Selecteer een betalingsmethode.
1. Verzend de bestelling.

<u>Verwachte resultaten</u>:

U kunt een bestelling verzenden.

<u>Werkelijke resultaten</u>:

U kunt geen bestelling verzenden. Het volgende [!DNL JS] de fout wordt getoond in het browser consolelogboek: &quot;*Geweigerd om inline manuscript uit te voeren omdat het de volgende richtlijn van het Beleid van de Veiligheid van de Inhoud schendt: &quot;manuscript-src..*&quot;

### Oorzaak

In Adobe Commerce en Magento Open Source versie 2.4.7 en hoger: **[!UICONTROL CSP]** is geconfigureerd in `restrict-mode`standaard, voor betalingspagina&#39;s in de opslagruimte en in de beheergebieden, en in `report-only` voor alle andere pagina&#39;s.
De overeenkomstige **[!UICONTROL CSP]** header bevat niet de `unsafe-inline` trefwoord in de `script-src` richtlijn voor betalingspagina&#39;s. Alleen [!DNL whitelisted] inline scripts zijn toegestaan.

### Oplossing

Gebruikers kunnen browserfouten zien als gevolg van bepaalde scripts die zijn geblokkeerd vanwege **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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
