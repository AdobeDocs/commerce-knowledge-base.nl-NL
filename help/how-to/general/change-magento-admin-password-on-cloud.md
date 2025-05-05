---
title: Beheerderswachtwoord wijzigen in Adobe Commerce op cloudinfrastructuur
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 7dc84525aef4d59346bb9bc980a7ed9b7f6612cf
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Beheerderswachtwoord wijzigen in Adobe Commerce op cloudinfrastructuur

## Methode 1: Uw wachtwoord vergeten (opnieuw instellen via e-mail)

![ login_panel_s.png ](assets/login_panel_s.png)

Lees de stappen in [ het Terugstellen van uw wachtwoordsectie van het Ondertekenen Admin ](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html?lang=nl-NL#admin-sign-in) in onze gebruikersgids.

Hieronder staan de kritische gebruiksopmerkingen.

### Uitgaande e-mails inschakelen

Alvorens **te gebruiken vergeten uw wachtwoord** vorm, [ uitgaande e-mails ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html?lang=nl-NL) toe gebruikend de [ Console van de Wolk ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=nl-NL).

### Controleer uw map voor ongewenste e-mail

Als u niet het bericht met een verbinding van het Wachtwoord van het Terugstellen kunt vinden, controleer uw *omslag van de Troep E-mail*. De naam van e-mail is *Bevestiging van het Terugstellen van het Wachtwoord voor Gebruikersnaam Admin*.

## Methode 2: Een nieuwe Admin-gebruiker toevoegen

Als u het wachtwoord voor de bestaande gebruiker niet kunt herstellen of opnieuw instellen, kunt u een nieuwe Admin-gebruiker maken en een wachtwoord voor deze gebruiker instellen. Voer daartoe de volgende stappen uit:

1. Gebruik [ SSH aan login aan het verre milieu ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=nl-NL).
1. Voer de volgende opdracht uit: `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
