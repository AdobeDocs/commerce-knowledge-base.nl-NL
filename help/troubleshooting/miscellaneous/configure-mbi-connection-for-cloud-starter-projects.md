---
title: Adobe Commerce Intelligence-verbinding configureren voor bestaande Cloud Starter-projecten
description: Dit artikel biedt een oplossing voor het gebruik van Adobe Commerce Intelligence-verbindingen voor een bestaand Cloud Starter-project.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Adobe Commerce Intelligence-verbinding configureren voor bestaande Cloud Starter-projecten

>[!NOTE]
>
>Adobe Commerce Intelligence stond voorheen bekend als Magento Business Intelligence (MBI).

Dit artikel biedt een oplossing voor het gebruik van Adobe Commerce Intelligence-verbindingen voor een bestaand Cloud Starter-project.

## Betrokken producten en versies

Adobe Commerce in de cloud starten (alle versies)

## Probleem

U wilt een Commerce Intelligence-verbinding configureren voor een bestaand Cloud Starter-project.

>[!NOTE]
>
>Adobe ondersteunt geen nieuwe Cloud Starter-abonnementen meer, maar als u een bestaand Starter-project hebt, moet u de onderstaande stappen volgen om de verbinding te configureren.

## Oplossing

Als u Commerce Intelligence for Cloud Starter-projecten wilt activeren, maakt u een Commerce Intelligence-account, maakt u een SSH-sleutel en maakt u verbinding met uw Adobe Commerce-database.

Voer de volgende stappen uit:

1. Je Adobe Commerce Intelligence-account maken:

   * Ga naar [ accounts.magento.com/customer/account/login ](https://account.magento.com/customer/account/login).
   * Ga naar **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * Klik op **[!UICONTROL Create Instance]** . Als u deze knoop niet ziet, contacteer uw Manager van het Succes van de Klant of Technische Adviseur van de Klant.
   * Selecteer uw Cloud Starter-abonnement. Als u alleen een Cloud Starter-abonnement hebt, wordt dit automatisch geselecteerd.
   * Klik op **[!UICONTROL Continue]**.
   * Voer uw gegevens in om uw account te maken.

   ![ creeer MBI rekening ](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * Ga naar je postvak IN en verifieer het e-mailadres.

   ![ verifieer e-mailadres ](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * Maak een wachtwoord.

   ![ creeer een wachtwoord ](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * Nadat u uw account hebt gemaakt, kunt u gebruikers toevoegen aan uw nieuwe account. Technische beheerders kunnen nu worden toegevoegd om de volgende stappen uit te voeren.

   ![ voeg gebruikers ](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png) toe

1. Voer gegevens in over de winkel om uw voorkeuren in te stellen.

   ![ voegt opslaginformatie ](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png) toe

   Er is wat informatie u zult moeten verzamelen alvorens u uw gegevensbestand voor de derde stap in de instapkaartstroom kunt verbinden. In stap 9 vult u de pagina *[!UICONTROL Connect your database]* in.

1. Maak een speciale Commerce Intelligence-gebruiker.

   * Creeer een nieuwe gebruiker op [ account.adobe.com ](https://account.adobe.com/).
   * Ga naar [ https://accounts.magento.com/customer/account/ ](https://accounts.magento.com/customer/account/) om uw rekening van Adobe Commerce te produceren.
   * Waarom een nieuwe gebruiker? Adobe Commerce Intelligence heeft een gebruiker nodig die aan het project wordt toegevoegd om onophoudelijk nieuwe gegevens te halen die naar het de gegevenspakhuis van Commerce Intelligence van de rekening moeten worden overgebracht. Deze gebruiker zal als die verbinding dienen. Het toevoegen van deze gebruiker aan het project zal in stap 4 komen.
   * De reden voor een speciale Commerce Intelligence-gebruiker is om te voorkomen dat de toegevoegde gebruiker per ongeluk wordt gedeactiveerd of verwijderd en de Commerce Intelligence-verbinding wordt gestopt.

1. Voeg de pas gecreëerde gebruiker aan het primaire milieu van het project als a *Medewerker* toe.

   ![ voeg gebruiker als Medewerker ](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png) toe

1. Haal de Commerce Intelligence SSH-toetsen op.

   * Ga naar de **[!UICONTROL Connect your database]** -pagina van de Commerce Intelligence-gebruikersinterface en blader omlaag naar **[!UICONTROL Encryption settings]** .
   * Kies **[!UICONTROL SSH Tunnel]** voor het veld **[!UICONTROL Encryption Type]** .
   * Van dropdown, kunt u de verstrekte Openbare Sleutel van de Hoofdzaak van de Hoofdzaak van Magento kopiëren en kleven BI.

   ![ de montages van de Encryptie ](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. Voeg uw nieuwe Openbare sleutel van de Hoofdzaak van Magento BI aan de gebruiker van Commerce Intelligence toe die in stap 5 wordt gecreeerd.

   * Ga naar [ accounts.magento.com/customer/account/login ](https://account.magento.com/customer/account/login). Meld u aan met uw aanmeldingsgegevens voor uw account voor de nieuwe Commerce Intelligence-gebruiker. Ga vervolgens naar de tab **[!UICONTROL Account Settings]** .
   * Schuif omlaag op de pagina en vouw de vervolgkeuzelijst voor SSH-toetsen uit. Klik vervolgens op **[!UICONTROL Add a public key]** .

   ![ voeg een openbare sleutel ](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png) toe

   * Voeg de Openbare Sleutel van SSH van de Hoofdzaak van Magento MBI van bovenaf toe.

   ![ voeg Openbare Sleutel SSH toe ](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Geef Business Intelligence Essentials [!DNL MySQL] gebruikersgegevens op.

   * Werk uw `.magento/services.yaml` bij.

   ```
   mysql:
    type: mysql:10.0
    disk: 2048
    configuration:
        schemas:
            - main
        endpoints:
            mysql:
                default_schema: main
                privileges:
                    main: admin
            mbi:
                default_schema: main
                privileges:
                    main: ro
   ```

   * Werk uw `.magento.app.yaml` bij.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. Haal informatie op voor het verbinden van uw database met Commerce Intelligence.

   Voer `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` uit om informatie op te halen over het verbinden van uw database.

   U ontvangt informatie die vergelijkbaar is met de onderstaande uitvoer:

   ```
   "mbi" : [
              {
                 "scheme" : "mysql",
                 "rel" : "mbi",
                 "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                 "query" : {
                    "is_master" : true
                 },
                 "ip" : "169.254.169.143",
                 "path" : "main",
                 "host" : "mbi.internal",
                 "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                 "username" : "mbi",
                 "service" : "mysql",
                 "port" : 3306,
                 "password" : "[password]"
              }
           ],
   ```

1. Verbind uw Adobe Commerce-database.

   ![ verbind uw Gegevensbestand van Adobe Commerce ](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *Inputs*:

   * De Naam van de integratie: [ kies een naam voor uw integratie.]
   * Host: `mbi.internal`
   * Poort: 3306
   * Gebruikersnaam: mbi
   * Wachtwoord: [ inputwachtwoord dat in de output van Stap 8 wordt verstrekt.]
   * Databasenaam: hoofd
   * De Voorvoegsels van de lijst: [ verlaten leeg als er geen lijstvoorvoegsels ] zijn

1. Stel de [!UICONTROL Timezone Settings] in.

   ![ montages van de Tijdzone ](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *Ingangen*

   * Database: Timezone: UTC
   * Gewenste Tijdzone: [ kies de tijdzone u uw gegevens binnen wilt tonen.]

1. Verkrijg informatie voor uw encryptie montages.

   * Het project UI verstrekt een SSH toegangstekenreeks. Deze tekenreeks kan worden gebruikt voor het verzamelen van de informatie die nodig is voor het externe adres en de gebruikersnaam bij het instellen van uw **[!UICONTROL Encryption settings]** . Selecteer **[!UICONTROL SSH]** om uw Gebruikersnaam en Verre Adres te zien. Het tekstkoord vóór *@* is uw Gebruikersnaam en het tekstkoord na *@* is uw Verre Adres.

   ![ de plaatsmeester van de Toegang ](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. Voer gegevens in voor uw [!UICONTROL Encryption Settings] .

   ![ de montages van de Encryptie ](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *Ingangen*

   * Type codering: SSH-tunnel
   * Extern adres: ssh.us-3.magento.cloud
   * Gebruikersnaam: vfbfui4vmfez6-master-7rqtwti—mymagento
   * Poort: 22

1. Klik op **[!UICONTROL Save Integration]**.
1. U hebt nu verbinding met uw Commerce Intelligence Essentials-account.
1. Als u een Adobe Commerce Intelligence Pro-klant bent, neemt u contact op met uw Customer Success Manager of Customer Technical Advisor om de volgende stappen te coördineren.

## Gerelateerde lezing

[ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
