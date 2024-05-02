---
title: Verbinding met Adobe Commerce Intelligence configureren voor bestaande Cloud Starter-projecten
description: Dit artikel biedt een oplossing voor het gebruik van een Adobe Commerce Intelligence-verbinding voor een bestaand Cloud Starter-project.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: b75328202952bf4c8f57ddc538b5c9e4318b2001
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Verbinding met Adobe Commerce Intelligence configureren voor bestaande Cloud Starter-projecten

>[!NOTE]
>
>Adobe Commerce Intelligence stond voorheen bekend als Magento Business Intelligence (MBI).

Dit artikel biedt een oplossing voor het gebruik van een Adobe Commerce Intelligence-verbinding voor een bestaand Cloud Starter-project.

## Betrokken producten en versies

Adobe Commerce in de cloud starten (alle versies)

## Probleem

U wilt een Commerce Intelligence-verbinding configureren voor een bestaand Cloud Starter-project.

>[!NOTE]
>
>Adobe ondersteunt geen nieuwe Cloud Starter-abonnementen meer, maar als u een bestaand Starter-project hebt, moet u de onderstaande stappen volgen om de verbinding te configureren.

## Oplossing

Als u Commerce Intelligence for Cloud Starter-projecten wilt activeren, maakt u een Commerce Intelligence-account, maakt u een SSH-sleutel en maakt u eindelijk verbinding met uw Adobe Commerce-database.

Voer de volgende stappen uit:

1. Je Adobe Commerce Intelligence-account maken:

   * Ga naar [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * Ga naar **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * Klik op de knop **[!UICONTROL Create Instance]**. Als u deze knoop niet ziet, contacteer uw Manager van het Succes van de Klant of Technische Adviseur van de Klant.
   * Selecteer uw Cloud Starter-abonnement. Als u alleen een Cloud Starter-abonnement hebt, wordt dit automatisch geselecteerd.
   * Klik op **[!UICONTROL Continue]**.
   * Voer uw gegevens in om uw account te maken.

   ![MBI-account maken](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * Ga naar je postvak IN en verifieer het e-mailadres.

   ![E-mailadres verifiëren](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * Maak een wachtwoord.

   ![Een wachtwoord maken](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * Nadat u uw account hebt gemaakt, kunt u gebruikers toevoegen aan uw nieuwe account. Technische beheerders kunnen nu worden toegevoegd om de volgende stappen uit te voeren.

   ![Gebruikers toevoegen](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png)

1. Voer gegevens in over de winkel om uw voorkeuren in te stellen.

   ![Winkelgegevens toevoegen](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png)

   Er is wat informatie u zult moeten verzamelen alvorens u uw gegevensbestand voor de derde stap in de instapkaartstroom kunt verbinden. U vult de *[!UICONTROL Connect your database]* pagina in stap 9.

1. Maak een speciale Commerce Intelligence-gebruiker.

   * Nieuwe gebruiker maken op [account.adobe.com](https://account.adobe.com/).
   * Ga naar [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/) om je Adobe Commerce-account te genereren.
   * Waarom een nieuwe gebruiker? Adobe Commerce Intelligence heeft een gebruiker nodig die aan het project wordt toegevoegd om voortdurend nieuwe gegevens op te halen die moeten worden overgedragen naar het Commerce Intelligence-gegevenspakhuis van de account. Deze gebruiker zal als die verbinding dienen. Het toevoegen van deze gebruiker aan het project zal in stap 4 komen.
   * De reden voor een speciale Commerce Intelligence-gebruiker is om te voorkomen dat de toegevoegde gebruiker per ongeluk wordt gedeactiveerd of verwijderd en de Commerce Intelligence-verbinding wordt verbroken.

1. Voeg de nieuwe gebruiker aan het primaire milieu van het project als toe *Medewerker*.

   ![Gebruiker toevoegen als medewerker](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. Haal je Commerce Intelligence SSH-sleutels in huis.

   * Ga naar de **[!UICONTROL Connect your database]** pagina van de Commerce Intelligence-ingestelde gebruikersinterface en schuiven omlaag naar **[!UICONTROL Encryption settings]**.
   * Voor het veld: **[!UICONTROL Encryption Type]**, kiest u **[!UICONTROL SSH Tunnel]**.
   * Van dropdown, kunt u de verstrekte Openbare Sleutel van de Hoofdzaak van de Hoofdzaak van Magento kopiëren en kleven BI.

   ![Versleutelingsinstellingen](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. Voeg uw nieuwe Openbare sleutel van de Hoofdzaak van Magento BI aan de gebruiker van de Intelligentie van Commerce toe die in stap 5 wordt gecreeerd.

   * Ga naar [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). Meld u aan met uw aanmeldingsgegevens voor uw account voor de nieuwe Commerce Intelligence-gebruiker. Ga vervolgens naar de **[!UICONTROL Account Settings]** tab.
   * Schuif omlaag op de pagina en vouw de vervolgkeuzelijst voor SSH-toetsen uit. Klik vervolgens op **[!UICONTROL Add a public key]**.

   ![Een openbare sleutel toevoegen](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * Voeg de Openbare Sleutel van SSH van de Hoofdzaak van Magento MBI van bovenaf toe.

   ![Openbare SSH-sleutel toevoegen](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Geef MySQL-gebruikersgegevens op voor Business Intelligence Essentials.

   * Werk uw `.magento/services.yaml`.

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

   * Werk uw `.magento.app.yaml`.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. Haal informatie op voor het verbinden van uw database met Commerce Intelligence.

   Uitvoeren `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` om informatie te krijgen over het verbinden van uw gegevensbestand.

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

   ![Verbinding maken met uw Adobe Commerce-database](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *Invoer*:

   * Integratienaam: [Kies een naam voor uw integratie.]
   * Host: `mbi.internal`
   * Poort: 3306
   * Gebruikersnaam: mbi
   * Wachtwoord: [invoerwachtwoord opgegeven in de uitvoer van Stap 8.]
   * Databasenaam: hoofd
   * Tabelvoorvoegsels: [leeg laten als er geen tabelvoorvoegsels zijn]

1. Stel uw [!UICONTROL Timezone Settings].

   ![Tijdzoneinstellingen](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *Invoer*

   * Database: Timezone: UTC
   * Gewenste tijdzone: [Kies de tijdzone waarin de gegevens moeten worden weergegeven.]

1. Verkrijg informatie voor uw encryptie montages.

   * Het project UI verstrekt een SSH toegangstekenreeks. Dit koord kan voor het verzamelen van de informatie nodig voor het Verre Adres en de Gebruikersnaam in vestiging worden gebruikt **[!UICONTROL Encryption settings]**. Selecteren **[!UICONTROL SSH]** om uw Naam van de Gebruiker en Verre Adres te zien. De tekstreeks voor de *@* is uw gebruikersnaam en de tekenreeks na *@* is uw Verre Adres.

   ![Site-master openen](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. Invoerinformatie voor uw [!UICONTROL Encryption Settings].

   ![Versleutelingsinstellingen](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *Invoer*

   * Type codering: SSH-tunnel
   * Extern adres: ssh.us-3.magento.cloud
   * Gebruikersnaam: vfbfui4vmfez6-master-7rqtwti—mymagento
   * Poort: 22

1. Klik op **[!UICONTROL Save Integration]**.
1. U hebt nu verbinding met uw Commerce Intelligence Essentials-account.
1. Als u een Adobe Commerce Intelligence Pro-klant bent, neemt u contact op met uw Customer Success Manager of Customer Technical Advisor om de volgende stappen te coördineren.
