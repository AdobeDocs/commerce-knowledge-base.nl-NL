---
title: Kan niet aanmelden bij Adobe Commerce-ondersteuning of cloudaccount
description: Dit artikel biedt een oplossing voor het aanmelden bij Adobe Commerce-ondersteuning of uw cloudproject.
exl-id: 676b32d2-8197-4c60-a1b1-3c51b01dd3a3
feature: Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Kan niet aanmelden bij Adobe Commerce-ondersteuning of cloudaccount

Dit artikel biedt een oplossing voor het aanmelden bij Adobe Commerce-ondersteuning of uw cloudproject.

## Betrokken producten en versies

Adobe Commerce (alle plaatsingsmethodes) alle [ gesteunde versies ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Probleem

Wanneer u naar [ https://account.magento.com/customer/account/login/ ](https://account.magento.com/customer/account/login/) of [ https://accounts.magento.cloud/user ](https://accounts.magento.cloud/user) gaat zou u kunnen opmerken dat er nu een verenigd login vorm is en u kunt niet meer uw geloofsbrieven ingaan zoals u eerder hebt.

<u> Stappen om </u> te reproduceren:

Meld u aan bij uw Commerce-account.

![ adobe-login-one ](assets/adobe-login-one.png)

<u> Verwacht resultaat </u>:

Aanmelden is gelukt.

<u> Werkelijk resultaat </u>:

Word omgeleid naar een pagina om u aan te melden met een Adobe-account en de gegevens werken niet.

![ adobe-login-two ](assets/adobe-login-two.png)


## Oorzaak

Als onderdeel van ons integratieproces van Adobe Commerce met andere oplossingen voor Adoben, moeten alle gebruikers een aanmeldingsnaam voor de Adobe maken - als ze er nog geen hebben - met hetzelfde e-mailadres dat is verbonden met hun MageID.

## Oplossing

U kunt zich aanmelden bij de account met:

- Een bestaande zakelijke/persoonlijke account van een Adobe.
- Als u geen Adobe-account hebt, maakt u een account met hetzelfde e-mailadres.

Voor stappen verwijzen naar [ Manager van de Identiteit van Commerce ](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-identity-manager.html) in Adobe Experience League.

## Gerelateerde lezing

- [Link Magento.com and accounts.magento.cloud account logins](/help/faq/general/linking-magento-com-and-accounts-magento-cloud-account-logins.md)
