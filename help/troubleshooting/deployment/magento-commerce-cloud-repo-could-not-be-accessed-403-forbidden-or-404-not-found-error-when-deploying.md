---
title: 'Adobe Commerce on cloud repo could not be access: 403 Forbidden or 404 Not found error when implementation'
description: 'In dit artikel wordt beschreven hoe u de Adobe Commerce op een mislukte implementatiefout voor een cloudinfrastructuur kunt oplossen, net als in het volgende:'
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# Adobe Commerce on cloud repo kan niet worden geopend: 403 Verboden of 404 Geen fout gevonden bij implementatie

In dit artikel wordt beschreven hoe u de implementatiefout van Adobe Commerce on cloud-infrastructuur kunt oplossen, vergelijkbaar met het volgende:

&quot;*&quot;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL kon niet worden betreden: HTTP/1.1 403 Verboden* &quot;. Of het &quot;*https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip&quot;dossier kon niet worden gedownload (HTTP/1.1 404 niet Gevonden)*&quot;.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.2.x, 2.3.x en 2.4.x

## Probleem

Foutbericht bij implementatie dat de repo-URL aangeeft, kan niet worden geopend.

<u> Stappen om te reproduceren </u>

Trigger plaatsing manueel of door een fusie, duw, of synchronisatie van uw milieu uit te voeren.

<u> Werkelijk resultaat </u>

Implementatie blijft vastzitten. In het login van de plaatsingsfout UI van het Project, wordt een foutenmelding gelijkend op het volgende getoond:

*&quot;De &#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL kon niet worden betreden: HTTP/1.1 \[403 Verboden of 404 Niet gevonden\]&quot;*.

(Klik op het pictogram &quot;Mislukt&quot; in de projectgebruikersinterface om het logbestand weer te geven.)

<u> Verwacht resultaat </u>

De implementatie is voltooid.

## Oorzaak

De fout wordt veroorzaakt door de toestemmingssleutels (toegangstoetsen) die ongeldig zijn, niet gespecificeerd of niet correct gespecificeerd.

Enkele redenen waarom sleutels niet geldig zijn zijn:

* U hebt de sleutels gegenereerd met uw gedeelde account.
* Uw licentie is eerder ingetrokken vanwege betalingsproblemen.

>[!NOTE]
>
>Neem contact op met het accountteam van de Adobe als dit te wijten is aan een factureringsprobleem of een probleem met een verlopen overeenkomst. Raadpleeg hiervoor een overzicht van de accountgegevens van de medewerker. Nadat uw licentie opnieuw is geactiveerd, worden uw support- en implementatierechten hersteld.

## Oplossing

Ga als volgt te werk om het probleem op te lossen met de machtigingstoetsen (zie de onderstaande secties voor meer informatie over elke stap):

1. Vraag de geldige autorisatietoetsen aan (sla deze over als u er absoluut zeker van bent dat uw sleutel geldig is).
1. Voeg de sleutelwaarde in de `env:COMPOSER_AUTH` variabele toe (of zorg ervoor dat de correcte waarde daar) is en controleer of de sleutels constant in de variabele op projectniveau en milieuniveau evenals het `auth.json` dossier (als het bestaat) in de projectwortel worden gespecificeerd.
1. Werk `auth.json` bij of verwijder dit om één plaats te hebben waar de sleutel wordt gevormd, als de waarden van de vergunningssleutels niet worden gespecificeerd of een andere waarde hebben.

### 1. Geldige autorisatietoetsen verkrijgen

Als u de sleutels gebruikte die onder de gedeelde rekening worden gecreeerd, moet u de de vergunningseigenaar van Adobe Commerce contacteren die u toegang verleent en verzoekt zij hen produceren de sleutels voor u.

Als uw vergunning eerder wegens betalingskwesties werd ingetrokken, en u die kwesties hebt opgelost en uw vergunning werd vernieuwd, moet u [ de nieuwe authentificatietoetsen ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) produceren.

### 2. Voeg de waarde van de toetsen toe aan de variabele env:COMPOSER\_AUTH en controleer of dezelfde toetsen zijn opgegeven in auth.json

Zie de instructies en de verwante informatie in [ uw bestaand systeem ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/overview) voorbereiden en [ authentificatietoetsen ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/overview) in onze ontwikkelaarsdocumentatie toevoegen.

### 3. Uth.json bijwerken of verwijderen

Hieronder volgt een stapsgewijze beschrijving van het bijwerken van uw verificatietoetsen:

1. Meld u aan bij de computer met de Adobe Commerce op SSH-sleutels voor cloudinfrastructuur.
1. Meld u aan bij uw project: `magento-cloud login`
1. Maak een vertakking om de code bij te werken (in het volgende voorbeeld wordt de vertakkingsnaam `auth` gemaakt van de primaire vertakking):     `magento-cloud environment:branch auth master`
1. Verandering in de folder van de projectwortel.
1. Facultatief: Schrap `auth.json` als u verkiest en aan [ stap 9 ](#step9) verdergaat.
1. Open `auth.json` in een teksteditor.

   ```json
              {
                "http-basic":  {
                    "repo.magento.com": {
                        "username": "<public_key>",
                        "password": "<private_key>"
                        }
                      }
                    }
   ```

1. Voeg de juiste verificatietoetsen toe.
1. Sla de wijzigingen op en sluit de teksteditor af.
1. Leg uw wijzigingen vast en voeg deze samen:

   `git add -A`

   `git commit -m "<message>"`

   `git push origin master`
1. Wacht op het project om op te stellen.
