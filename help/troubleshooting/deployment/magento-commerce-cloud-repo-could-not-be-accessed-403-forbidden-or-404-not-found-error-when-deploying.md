---
title: 'Adobe Commerce on cloud repo could not be access: 403 Forbidden or 404 Not found error when implementation'
description: 'In dit artikel wordt beschreven hoe u de Adobe Commerce op een mislukte implementatiefout voor een cloudinfrastructuur kunt oplossen, net als in het volgende:'
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Adobe Commerce on cloud repo kan niet worden geopend: 403 Verboden of 404 Geen fout gevonden bij implementatie

In dit artikel wordt beschreven hoe u de implementatiefout van Adobe Commerce on cloud-infrastructuur kunt oplossen, vergelijkbaar met het volgende:

&quot;*Kan de URL &#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39;&#39; niet openen: HTTP/1.1 403 Verboden* &quot;. Of de &quot;*https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip&quot; kan niet worden gedownload (HTTP/1.1 404 niet gevonden)*&quot;.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.2.x, 2.3.x en 2.4.x

## Probleem

Foutbericht bij implementatie dat de repo-URL aangeeft, kan niet worden geopend.

<u>Stappen om te reproduceren</u>

Trigger plaatsing manueel of door een fusie, duw, of synchronisatie van uw milieu uit te voeren.

<u>Werkelijk resultaat</u>

Implementatie blijft vastzitten. In het login van de plaatsingsfout UI van het Project, wordt een foutenmelding gelijkend op het volgende getoond:

*&quot;De URL &#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; kan niet worden geopend: HTTP/1.1 \[403 Verboden of 404 Niet gevonden\]&quot;*.

(Klik op het pictogram &quot;Mislukt&quot; in de projectgebruikersinterface om het logbestand weer te geven.)

<u>Verwacht resultaat</u>

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
1. Voeg de sleutelwaarde in toe `env:COMPOSER_AUTH` variabele (of controleer of de juiste waarde aanwezig is) en controleer of de toetsen consistent zijn opgegeven in de variabele en het dialoogvenster `auth.json` bestand in de hoofdmap van het project.
1. Bijwerken of verwijderen `auth.json`, om één enkele plaats te hebben waar de sleutel wordt gevormd, als de waarden van de vergunningssleutels niet worden gespecificeerd of een andere waarde hebben.

### 1. Geldige autorisatietoetsen verkrijgen

Als u de sleutels gebruikte die onder de gedeelde rekening worden gecreeerd, moet u de de vergunningseigenaar van Adobe Commerce contacteren die u toegang verleent en verzoekt zij hen produceren de sleutels voor u.

Als uw licentie eerder is ingetrokken vanwege betalingsproblemen en u deze problemen hebt opgelost en uw licentie is vernieuwd, moet u [nieuwe verificatietoetsen genereren](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html).

### 2. Voeg de waarde van de toetsen toe aan de variabele env:COMPOSER\_AUTH en controleer of dezelfde toetsen zijn opgegeven in auth.json

Zie de instructies en verwante informatie in [Uw bestaande systeem voorbereiden](https://devdocs.magento.com/cloud/setup/first-time-setup-import-prepare.html#auth-json) en [Verificatietoetsen toevoegen](https://devdocs.magento.com/cloud/setup/first-time-setup-import-prepare.html#add-authentication-keys) in onze ontwikkelaarsdocumentatie.

### 3. Uth.json bijwerken of verwijderen

Hieronder volgt een stapsgewijze beschrijving van het bijwerken van uw verificatietoetsen:

1. Meld u aan bij de computer met de Adobe Commerce op SSH-sleutels voor cloudinfrastructuur.
1. Meld u aan bij uw project: `magento-cloud login`
1. Een vertakking maken om de code bij te werken (in het volgende voorbeeld is de vertakkingsnaam `auth` wordt gemaakt van de primaire vertakking):     `magento-cloud environment:branch auth master`
1. Verandering in de folder van de projectwortel.
1. Optioneel: verwijder de `auth.json` als u dit wilt en wilt doorgaan [stap 9](#step9).
1. Openen `auth.json` in een teksteditor.

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
