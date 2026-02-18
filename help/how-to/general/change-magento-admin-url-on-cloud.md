---
title: Admin-URL wijzigen in Adobe Commerce op cloudinfrastructuur
description: Standaard is de URL [Commerce Admin](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/admin/admin) ingesteld op *&lt;domain_name&gt;/admin*. In dit artikel wordt weergegeven hoe u de URL kunt wijzigen.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Admin-URL wijzigen in Adobe Commerce op cloudinfrastructuur

Door gebrek, wordt [&#x200B; Commerce Admin &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html?lang=nl-NL) URL geplaatst aan *&lt;domain\_name>/admin*. In dit artikel wordt weergegeven hoe u de URL kunt wijzigen.

## Methode 1: Wijzigen met de beheerfunctie

Lees de stappen: [&#x200B; Gebruikend een Douane Admin URL > Verandering van Admin &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=nl-NL#use-a-custom-admin-url) in onze gebruikersgids.

## Methode 2: ADMIN\_URL-omgevingsvariabele toevoegen

### Integratieomgeving

Van de [&#x200B; Console van de Wolk &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=nl-NL), voeg een nieuwe variabele met toe:

**Naam:** ADMIN\_URL **Waarde:** nieuwe Admin URL

* Voor gedetailleerde stappen, zie [&#x200B; milieuvariabelen &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=nl-NL#configure-environment) in onze ontwikkelaarsdocumentatie toevoegen.
* Ook verwijs naar [&#x200B; milieuvariabelen &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.

### Als Staging en productie niet beschikbaar zijn in de cloud-console

[&#x200B; voorlegt een steunkaartje &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) verzoekend om de variabele ADMIN\_URL voor uw het Opvoeren of milieu van de Productie toe te voegen.

Als het Opvoeren en de Productie toegankelijk zijn van de Console van de Wolk, voeg de Variabele van het Milieu toe zoals die in de *milieu* sectie hierboven van de Integratie wordt beschreven.

### Variabelen toevoegen met Cloud CLI

U kunt de ADMIN\_URL-variabele toevoegen met de volgende Cloud CLI-opdracht (voor hoofd):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Voor meer gedetailleerde instructies, verwijs naar [&#x200B; Verandering Admin URL &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=nl-NL#change-the-admin-url) in het Admin veranderingenonderwerp in Commerce op de Gids van de Infrastructuur van de Wolk.

Houd er rekening mee dat het gebruik van de Cloud CLI om de ADMIN\_URL-variabele te wijzigen, leidt tot een herimplementatie van de omgeving. Variabelen kunnen standaard worden overgeërfd. Om overerving te voorkomen, gebruikt u de opdrachtopties van Cloud CLI om aan te geven dat u niet wilt dat de waarde van de variabele door onderliggende omgevingen wordt overgenomen. Verwijs naar het [&#x200B; 1&rbrace; onderwerp van de Zichtbaarheid &lbrace;in Variabele niveaus in Commerce op de Gids van de Infrastructuur van de Wolk.](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=nl-NL#visibility)
