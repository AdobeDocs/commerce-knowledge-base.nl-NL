---
title: Herplaatsing van omgeving is mislukt of MySQL-server is weggegaan
description: Dit artikel biedt een oplossing voor Adobe Commerce-problemen (alle implementatiemethoden), waarbij de hoeveelheid ruimte die voor MySQL is toegewezen, leidt tot vastgelopen implementatiefouten of verbindingsfouten in de database.
exl-id: 2086b45a-0bfe-45cc-bef9-1b6f09ddb70a
feature: Deploy, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Herplaatsing van omgeving is mislukt of MySQL-server is weggegaan

Dit artikel biedt een oplossing voor Adobe Commerce-problemen (alle implementatiemethoden), waarbij de hoeveelheid ruimte die voor MySQL is toegewezen, leidt tot vastgelopen implementatiefouten of verbindingsfouten in de database.

## Betrokken producten en versies

* Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur (alle versies)

## Probleem

* Implementeer proces mislukt met de volgende fout in het implementatielogboek (opdrachtregel en UI-logbestand):  ```bash    Re-deploying environment abcdefghijklm-master-7rqtwti         E: Environment redeployment failed    ```
* Adobe Commerce reageert met 503-fout en het volgende foutbericht wordt weergegeven in toepassingslogboeken:    ```bash    SQLSTATE[HY000] [2006] MySQL server has gone away    ```    en de volgende fout verschijnt wanneer u met een server MySQL verbindt:    ```bash    ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"    ```

## Oorzaak

De meest waarschijnlijke oorzaak van de kwesties is het MySQL gegevensbestand toegewezen ruimte die te laag is. Om dit te verzekeren is het geval, controleer de ruimte beschikbaar voor MySQL zoals verder beschreven.

### Controleer of er voldoende ruimte is voor MySQL

Voor alle Adobe Commerce op de Starter-architectuuromgevingen van de cloud-infrastructuur, en [Integratieomgeving](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) van de Adobe Commerce over cloudinfrastructuur Pro, [SSH voor het milieu](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) en voer de opdracht uit:

```bash
magento-cloud db:size
```

Voor de Staging- of Productieomgeving van de Pro-architectuur [SSH voor het milieu](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)en voert u de `df -h`   `| grep mysql` gebruiken. Het resultaat ziet er ongeveer als volgt uit:

```bash
sxpe7gigd5ok2@i-00baa9e24f31dba41:~$ df -h | grep mysql
/dev/xvdj                            40G  7.4G   32G  19% /data/mysql
```

## Oplossing

### Om de kwestie op te lossen, moet u meer ruimte voor MySQL toewijzen.

Voor alle Starter-architectuur en Pro-architectuurintegratieomgevingen gebeurt dit in de `.magento/services.yaml` bestand, door de `mysql: disk:` parameter. Bijvoorbeeld:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Zie de [MySQL-service instellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html) artikel ter referentie.

Als u deze wijzigingen wilt aanbrengen in de omgeving Staging of Productie van de Pro-architectuur, moet u een [Ondersteuningsticket](https://support.magento.com). Maar doorgaans hoeft u dit niet te doen bij het opslaan/produceren van de Pro-architectuur, aangezien Adobe Commerce deze parameters voor u controleert en u waarschuwt en/of acties uitvoert volgens het contract.

### Wijzigingen toepassen

Wanneer u de `.magento/services.yaml` moet u de wijzigingen vastleggen en doorvoeren voordat deze kunnen worden toegepast. De duw zal het plaatsingsproces teweegbrengen.
