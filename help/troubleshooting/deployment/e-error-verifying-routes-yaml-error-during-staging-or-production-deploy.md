---
title: 'E: Fout bij het controleren van routes.yaml-fout tijdens het implementeren van testversies of productieprocessen'
description: 'Dit artikel biedt een oplossing voor het probleem van de Adobe Commerce met betrekking tot de cloudinfrastructuur, waarbij u het foutbericht *"E: Error while checking routes.yaml"* krijgt wanneer u probeert het project te implementeren in de omgeving van Staging of Production.'
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E: Fout bij het controleren van routes.yaml-fout tijdens het implementeren van testversies of productieprocessen

Dit artikel verstrekt een oplossing voor de Adobe Commerce op de kwestie van de wolkeninfrastructuur, waar u *&quot;E: Fout terwijl het verifiëren van* foutenmelding {bij het proberen om het project aan het het Opvoeren of milieu van de Productie op te stellen krijgt.

## Betrokken versies

* Adobe Commerce op cloud-infrastructuur, alle versies

## Probleem

<u> Stappen om </u> te reproduceren:

Trigger opstellen door de code aan het Staging of milieu van de Productie te duwen.

<u> Verwacht gedrag </u>:

Implementatie is geslaagd.

<u> Ware gedrag </u>:

De plaatsing wordt geblokkeerd en het volgende foutenbericht wordt getoond in het logboek:

<pre>Het opstellen van toepassingen die configuratie E verifiëren: Fout terwijl het verifiëren van routes.yaml.
De volgende domeinen worden gevormd voor uw cluster, maar hebben geen routes die in uw routes.yaml- dossier worden bepaald:

- store1.example.com
- store2.example.com
- test-store.example.com

Met uw huidige configuratie routes.yaml,
  Deze domeinen zouden NIET worden gediend!

Zie hier voor instructies voor het oplossen van problemen om door te gaan:
 /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## Oorzaak

Deze fout treedt op als de routeconfiguratie voor andere domeinen die aan uw project zijn toegevoegd, ontbreekt in het `routes.yaml` -bestand.

Als deel van de zelfbediening van Adobe Commerce enablement verbetering voor zelfbediening routeconfiguratie, hebben wij een pre-plaatsingscontrole toegevoegd om ervoor te zorgen dat alle domeinen in uw project routes hebben die in het `routes.yaml` dossier worden gevormd. Als om het even welke domeinen routeconfiguratie missen, wordt de plaatsing geblokkeerd.

## Oplossing

Om de geblokkeerde plaatsing op te lossen, werk het `routes.yaml` dossier bij om routes voor de domeinen te vormen die in het foutenbericht door één van beiden van de volgende methodes worden vermeld:

* Pas de patch toe die door Adobe Commerce is geleverd tijdens het upgradeproces.
* Voeg handmatig de ontbrekende routeconfiguratie toe aan het `routes.yaml` -bestand.

### Methode 1: De door Adobe Commerce geleverde patch toepassen

1. Zoek een recent de steunkaartje van Adobe Commerce met de titel &quot;*laat zelfdiensteigenschappen voor &lt;project\_ID>&quot;toe.*
1. Volg de instructies in het kaartje om de patch toe te passen, die de routeconfiguratie voor uw wolkenmilieu bijwerkt.
1. С en duw op de veranderingen om uw project opnieuw op te stellen.

### Methode 2: voeg manueel de ontbrekende routeconfiguratie toe

1. Om alle domeinen in uw project te dienen gebruikend de zelfde routeconfiguratie, werk het `routes.yaml` dossier bij toevoegend routesjablonen voor het standaarddomein en alle andere domeinen op uw project zoals aangetoond in het volgende voorbeeld:

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. С en duw op uw wijzigingen om uw project opnieuw te implementeren.

Voor gedetailleerde instructies om de routeconfiguratie bij te werken, zie [ Wolk voor Adobe Commerce > routes ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml) in onze ontwikkelaarsdocumentatie vormen.

>[!NOTE]
>
>Als uw projectconfiguratie domeinen specificeert die niet meer in gebruik zijn, voltooi de volgende stappen om hen uit uw project bij uw vroegst gemak te verwijderen: 1. Verzend een ondersteuningsticket met een lijst met domeinen die u uit uw projectomgevingen wilt verwijderen. 2. Nadat het ondersteuningsteam de domeinen heeft verwijderd, werkt u het `routes.yaml` -bestand bij om verwijzingen naar verouderde domeinen te verwijderen.
