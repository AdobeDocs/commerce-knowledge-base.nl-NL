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

![login_panel_s.png](assets/login_panel_s.png)

Lees de stappen in het dialoogvenster [Wachtwoordsectie voor aanmelden bij beheerder opnieuw instellen](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html#admin-sign-in) in onze gebruikershandleiding.

Hieronder staan de kritische gebruiksopmerkingen.

### Uitgaande e-mails inschakelen

Voordat u de **Uw wachtwoord vergeten** formulier, [uitgaande e-mails inschakelen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html) met de [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

### Controleer uw map voor ongewenste e-mail

Als u het bericht niet kunt vinden met de koppeling Wachtwoord opnieuw instellen, controleert u *Junk Email* map. De naam van de e-mail is *Bevestiging voor opnieuw instellen van wachtwoord voor Admin-gebruikersnaam*.

## Methode 2: Een nieuwe Admin-gebruiker toevoegen

Als u het wachtwoord voor de bestaande gebruiker niet kunt herstellen of opnieuw instellen, kunt u een nieuwe Admin-gebruiker maken en een wachtwoord voor deze gebruiker instellen. Voer daartoe de volgende stappen uit:

1. Gebruiken [SSH voor aanmelding bij de externe omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Voer de volgende opdracht uit: `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
