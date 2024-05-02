---
title: 'E: Fout bij het controleren van routes.yaml-fout tijdens het implementeren van testversies of productieprocessen.'
description: 'Dit artikel biedt een oplossing voor het probleem met de Adobe Commerce op het gebied van de cloudinfrastructuur, waarbij u de foutmelding *"E: Error while checking routes.yaml"* krijgt wanneer u probeert het project te implementeren in de omgeving van Staging of Production.'
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E: Fout bij het controleren van routes.yaml-fout tijdens het implementeren van testversies of productieprocessen

Dit artikel biedt een oplossing voor het Adobe Commerce-probleem met cloudinfrastructuur, waar u de *&quot;E: Fout bij het controleren van routes.yaml&quot;* foutbericht bij het implementeren van het project in de omgeving van Staging of Productie.

## Betrokken versies

* Adobe Commerce op cloud-infrastructuur, alle versies

## Probleem

<u>Stappen om te reproduceren</u>:

Trigger opstellen door de code aan het Staging of milieu van de Productie te duwen.

<u>Verwacht gedrag</u>:

Implementatie is geslaagd.

<u>Werkelijk gedrag</u>:

De plaatsing wordt geblokkeerd en het volgende foutenbericht wordt getoond in het logboek:

<pre>Het opstellen van toepassingen die configuratie E verifiëren: Fout terwijl het verifiëren van routes.yaml.
De volgende domeinen worden gevormd voor uw cluster, maar hebben geen routes die in uw routes.yaml- dossier worden bepaald: - store1.example.com - store2.example.com - test-store.example.com met uw huidige routes.yaml configuratie, zouden deze domeinen NIET worden gediend!

Raadpleeg hier voor instructies voor het oplossen van problemen: /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## Oorzaak

Deze fout komt voor als de routeconfiguratie voor om het even welke extra domeinen die aan uw project zijn toegevoegd van mist `routes.yaml` bestand.

Als deel van de zelfbediening van Adobe Commerce enablement verbetering voor zelfbediening routeconfiguratie, hebben wij een pre-plaatsingscontrole toegevoegd om ervoor te zorgen dat alle domeinen in uw project routes hebben die in worden gevormd `routes.yaml` bestand. Als om het even welke domeinen routeconfiguratie missen, wordt de plaatsing geblokkeerd.

## Oplossing

Om de geblokkeerde implementatie op te lossen, werkt u de `routes.yaml` dossier om routes voor de domeinen te vormen die in het foutenbericht door één van beiden van de volgende methodes worden vermeld te gebruiken:

* Pas de patch toe die door Adobe Commerce is geleverd tijdens het upgradeproces.
* Voeg manueel de ontbrekende routeconfiguratie aan toe `routes.yaml` bestand.

### Methode 1: De door Adobe Commerce geleverde patch toepassen

1. Zoek een recent Adobe Commerce-ondersteuningsticket met de titel &quot;*Functies voor zelfbediening inschakelen voor &lt;project _id=&quot;&quot;>&quot;.*
1. Volg de instructies in het kaartje om de patch toe te passen, die de routeconfiguratie voor uw wolkenmilieu bijwerkt.
1. С en duw op de veranderingen om uw project opnieuw op te stellen.

### Methode 2: voeg manueel de ontbrekende routeconfiguratie toe

1. Om alle domeinen in uw project te dienen gebruikend de zelfde routeconfiguratie, werk update `routes.yaml` dossier die routesjablonen voor het standaarddomein en alle andere domeinen op uw project toevoegen zoals aangetoond in het volgende voorbeeld:

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. С en duw op uw wijzigingen om uw project opnieuw te implementeren.

Voor gedetailleerde instructies om de routeconfiguratie bij te werken, zie [Cloud voor Adobe Commerce > routes configureren](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_routes.html) in onze ontwikkelaarsdocumentatie.

>[!NOTE]
>
>Als uw projectconfiguratie domeinen specificeert die niet meer in gebruik zijn, voltooi de volgende stappen om hen uit uw project bij uw vroegst gemak te verwijderen: 1. Verzend een ondersteuningsticket met een lijst met domeinen die u uit uw projectomgevingen wilt verwijderen. 2. Wanneer het ondersteuningsteam de domeinen heeft verwijderd, werkt u de `routes.yaml` bestand om verwijzingen naar verouderde domeinen te verwijderen.
