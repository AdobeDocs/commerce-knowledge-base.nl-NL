---
title: Admin-URL wijzigen in Adobe Commerce op cloudinfrastructuur
description: Standaard is de URL [Commerce Admin](https://docs.magento.com/m2/ee/user_guide/stores/admin.html) ingesteld op *&lt;domain\_name&gt;/admin*. In dit artikel wordt weergegeven hoe u de URL kunt wijzigen.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 04dba4e2adeaaa7649b817444024bf96e7830ad3
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Admin-URL wijzigen in Adobe Commerce op cloudinfrastructuur

Standaard worden de [Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) URL is ingesteld op *&lt;domain _name=&quot;&quot;>/admin*. In dit artikel wordt weergegeven hoe u de URL kunt wijzigen.

## Methode 1: Wijzigen met de beheerfunctie

Lees de stappen: [Een aangepaste Admin-URL gebruiken > Wijzigen vanuit de Admin](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) in onze gebruikershandleiding.

## Methode 2: ADMIN\_URL-omgevingsvariabele toevoegen

### Integratieomgeving

Van de [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html)voegt u een nieuwe variabele toe met:

**Naam:** ADMIN\_URL **Waarde:** new Admin URL

* Zie voor meer informatie [omgevingsvariabelen toevoegen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) in onze ontwikkelaarsdocumentatie.
* Zie ook [omgevingsvariabelen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) in onze ontwikkelaarsdocumentatie.

### Als Staging en productie niet beschikbaar zijn in de cloud-console

[Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) aanvragen om de ADMIN\_URL-variabele toe te voegen voor uw testomgeving.

Als Staging en productie toegankelijk zijn vanuit de cloud-console, voegt u de omgevingsvariabele toe, zoals beschreven in het dialoogvenster *Integratieomgeving* hierboven.

### Variabelen toevoegen met Cloud CLI

U kunt de ADMIN\_URL-variabele toevoegen met de volgende Cloud CLI-opdracht (voor hoofd):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Raadpleeg voor meer gedetailleerde instructies [De URL van de beheerder wijzigen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) in het onderwerp Admin variables in de Commerce on Cloud Infrastructure Guide.

Houd er rekening mee dat het gebruik van de Cloud CLI om de ADMIN\_URL-variabele te wijzigen, leidt tot een herimplementatie van de omgeving. Variabelen kunnen standaard worden overgeërfd. Om overerving te voorkomen, gebruikt u de opdrachtopties van Cloud CLI om aan te geven dat u niet wilt dat de waarde van de variabele door onderliggende omgevingen wordt overgenomen. Zie de [Zichtbaarheid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) onderwerp in variabele niveaus in de Commerce on Cloud Infrastructure Guide.
