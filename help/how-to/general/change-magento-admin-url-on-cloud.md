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

Door gebrek, wordt [ Commerce Admin ](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) URL geplaatst aan *&lt;domain\_name>/admin*. In dit artikel wordt weergegeven hoe u de URL kunt wijzigen.

## Methode 1: Wijzigen met de beheerfunctie

Lees de stappen: [ Gebruikend een Douane Admin URL > Verandering van Admin ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) in onze gebruikersgids.

## Methode 2: ADMIN\_URL-omgevingsvariabele toevoegen

### Integratieomgeving

Van de [ Console van de Wolk ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html), voeg een nieuwe variabele met toe:

**Naam:** ADMIN\_URL **Waarde:** nieuwe Admin URL

* Voor gedetailleerde stappen, zie [ milieuvariabelen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) in onze ontwikkelaarsdocumentatie toevoegen.
* Ook verwijs naar [ milieuvariabelen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) in onze ontwikkelaarsdocumentatie.

### Als Staging en productie niet beschikbaar zijn in de cloud-console

[ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) verzoekend om de variabele ADMIN\_URL voor uw het Opvoeren of milieu van de Productie toe te voegen.

Als het Opvoeren en de Productie toegankelijk zijn van de Console van de Wolk, voeg de Variabele van het Milieu toe zoals die in de *milieu* sectie hierboven van de Integratie wordt beschreven.

### Variabelen toevoegen met Cloud CLI

U kunt de ADMIN\_URL-variabele toevoegen met de volgende Cloud CLI-opdracht (voor hoofd):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Voor meer gedetailleerde instructies, verwijs naar [ Verandering Admin URL ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) in het Admin veranderingenonderwerp in Commerce op de Gids van de Infrastructuur van de Wolk.

Houd er rekening mee dat het gebruik van de Cloud CLI om de ADMIN\_URL-variabele te wijzigen, leidt tot een herimplementatie van de omgeving. Variabelen kunnen standaard worden overgeërfd. Om overerving te voorkomen, gebruikt u de opdrachtopties van Cloud CLI om aan te geven dat u niet wilt dat de waarde van de variabele door onderliggende omgevingen wordt overgenomen. Verwijs naar het [ 1} onderwerp van de Zichtbaarheid {in Variabele niveaus in Commerce op de Gids van de Infrastructuur van de Wolk.](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility)
