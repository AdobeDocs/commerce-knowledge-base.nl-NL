---
title: PayPal Payflow Pro actieve carding-activiteiten
description: BIJGEWERKT OP 2 april 2019
exl-id: 9fe73788-5b67-445a-9b0d-86489125d271
feature: Cache, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# PayPal Payflow Pro actieve carding-activiteiten

BIJGEWERKT OP 2 april 2019

De integratie van PayPal Payflow Pro in Adobe Commerce wordt actief aangegrepen door carding activity, waarbij aanvallers honderden $0 transacties met gestolen creditcards proberen te controleren op de geldigheid van de kaart.

De activiteit richt momenteel versies van deze integratie van Payflow Pro die in Adobe Commerce 2.1.x, 2.2.x, 2.3.x voor Magento Open Source en Commerce (op-gebouw en wolk) inbegrepen waren. De kaardbewerking is inherent aan de manier waarop Payflow Pro is geïntegreerd in winkelwagentjes.

>[!NOTE]
>
>Om deze problemen op te lossen, hebben we nieuwe Composer-pakketten beschikbaar gesteld om Google reCAPTCHA of CAPTCHA toe te voegen aan het uitbetalingsformulier van Payflow Pro. We raden u aan deze pakketten op alle Adobe Commerce-versies en -versies te installeren.

Dit probleem is van toepassing op de volgende Adobe Commerce-versies:

* Adobe Commerce op locatie v2.1.x, 2.2.x, 2.3.x
* Adobe Commerce op cloud-infrastructuur v2.1.x, 2.2.x, 2.3.x

## Probleem

Symptomen van deze aanvallen zijn:

* Je PayPal Payflow Pro-rekening toont honderden frauduleuze transacties die zijn geïdentificeerd
* PayPal kan een Payflow Pro-rekening opschorten wegens inkomende fraudetransacties en aanzienlijke kosten in rekening brengen

## Oplossing

Ter bescherming tegen deze aanvallen raden we u aan om Google reCAPTCHA (aanbevolen) of CAPTCHA toe te voegen aan het afhandelingsformulier van Payflow Pro. Dit omvat het installeren van de Composer-pakketten en het configureren van Google reCAPTCHA of CAPTCHA in Commerce Admin.

### Pakketten installeren

Adobe heeft twee pakketopties gemaakt om Google reCAPTCHA en/of CAPTCHA toe te voegen aan het afhandelingsformulier van Payflow Pro. Als u een van deze pakketten installeert, worden de huidige installaties bijgewerkt en wordt een optie toegevoegd die deze beveiliging kan verbeteren voor het uitbetalingsformulier van Payflow Pro.

Deze pakketten zijn compatibel met de volgende Adobe Commerce-implementaties en -versies:

Adobe Commerce (alle implementatiemethoden) en Magento Open Source 2.1.x, 2.2.x, 2.3.x

Voor de installatie zijn CLI-opdrachten vereist voor uw Adobe Commerce-instantie. Mogelijk is hulp van ontwikkelaars vereist.

>[!NOTE]
>
>We raden u aan om Google reCAPTCHA te installeren en te configureren, naast de installatie van relevante Payflow Pro-updates voor het afhandelingsformulier. Deze optie biedt een onzichtbare controle en meerdere configuratieopties.

#### Google reCAPTCHA installeren en formulierupdates uitchecken

Het `magento/module-paypal-recaptcha` -pakket bevat integratie met updates van Google reCAPTCHA- en Payflow Pro-betalingsformulieren. Zelfs als u de reCAPTCHA module geïnstalleerd en gevormd hebt, adviseren wij u dit pakket te installeren.

Voer de volgende opdrachten uit om de toepassing te installeren.

**voor Adobe Commerce op-gebouw:**

```bash
composer require magento/module-paypal-recaptcha
bin/magento module:enable Magento_PaypalReCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**voor Adobe Commerce op wolkeninfrastructuur:**

1. Voer de volgende opdracht uit:

   ```bash
   composer require magento/module-paypal-recaptcha
   ```

1. Wijzigingen vastleggen en duwen:

   ```bash
   git add -A && git commit -m "Install Google reCAPTCHA"    git push origin %branch_name%
   ```

1. Wacht tot de implementatie is voltooid.

#### Uitchecken van formulierupdates voor CAPTCHA installeren

Het pakket `magento/module-paypal-captcha` bevat integratie met de native Adobe Commerce CAPTCHA-module.

Voer de volgende opdrachten uit om de toepassing te installeren:

**voor Adobe Commerce op-gebouw:**

```bash
composer require magento/module-paypal-captcha
bin/magento module:enable Magento_PaypalCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**voor Adobe Commerce op wolkeninfrastructuur:**

1. Voer de volgende opdracht uit:

   ```bash
   composer require magento/module-paypal-captcha
   ```

1. Wijzigingen vastleggen en duwen:

   ```bash
   git add -A && git commit -m "Install CAPTCHA"    git push origin %branch_name%
   ```

1. Wacht tot de implementatie is voltooid.

### Google reCAPTCHA of CAPTCHA configureren

Nadat u het pakket hebt geïnstalleerd, configureert u Google reCAPTCHA (aanbevolen) of CAPTCHA zoals beschreven in de volgende documenten:

* [ Google reCAPTCHA ](https://docs.magento.com/user-guide/stores/security-google-recaptcha.html) in onze gebruikersgids.
* [ CAPTCHA ](https://docs.magento.com/user-guide/stores/security-captcha.html) in onze gebruikersgids.

De nieuwe optie voor het uitcheckformulier is:

* Google reCAPTCHA: gebruiken in PayPal Payflow Pro-betalingsformulier
* CAPTCHA: Payflow Pro

## PayPal-ondersteuning en contactpersonen

Neem contact op met PayPal Payflow Merchant Support voor meer informatie over de services voor fraudebescherming. U kunt het team van de Steun van PayPal verzoeken om ](https://developer.paypal.com/api/nvp-soap/payflow/fraud-protection/) filters van de Bescherming van de Fraude toe te laten Basis om de strengste controle mogelijk over betalingen te verstrekken zodat u automatisch betalingen kunt ontkennen die waarschijnlijk in frauduleuze transacties zullen resulteren en betalingen goedkeuren die geen typisch probleem zijn. [ Houd er rekening mee dat transacties na het inschakelen van de filters van PayPal Fraud Protection Services maximaal twee uur kunnen duren.

>[!NOTE]
>
>Zie voor meer informatie de KB [ van PayPal&#39;s &quot;Adobe heeft contact met me opgenomen over mijn Payflow Pro-integratie. Wat moet ik doen?&quot;](https://www.paypal.com/us/smarthelp/article/ts2242).

**PayPal de Informatie van de Steun van de Betalingsindustrie van de Betalingsverkeer**

De kantooruren van de Steun van de koophandel zijn van maandag tot vrijdag van 7:00 - 8:00 PM CST. Je kunt contact opnemen met Payflow Merchant Support voor hulp via je account via telefoon of e-mail:

* Telefoon: 1-888-883-9770 (Selecteer vraag 2)
* Internationale klanten: 1-408-967-0191
* E-mail: [ payflow-support@paypal.com](mailto:payflow-support@paypal.com)

Australische ondersteuning

* Maandag - vrijdag 8:00 - 19:00 uur (AU-tijd)
* Telefoon: +61 2 8288 0198
* E-mail: [ gateway-ausupport@paypal.com](mailto:gateway-ausupport@paypal.com)
