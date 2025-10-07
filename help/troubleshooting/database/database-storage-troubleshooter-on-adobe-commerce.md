---
title: Problemen met opslagproblemen voor databases op Adobe Commerce oplossen
description: Dit artikel is een hulpprogramma voor het oplossen van problemen voor klanten in Adobe Commerce die problemen hebben met databases. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen. Afhankelijk van uw symptomen en configuratie, zal de probleemoplosser verklaren hoe te om ruimte en configuratiekwesties met gegevensbestanden problemen op te lossen.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: aa4cfbceb745f1a06b8a8f9e93cbdebbc151458b
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# Problemen met opslagproblemen voor databases op Adobe Commerce oplossen

Dit artikel is een hulpprogramma voor het oplossen van problemen voor klanten in Adobe Commerce die problemen hebben met databases. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen. Afhankelijk van uw symptomen en configuratie, zal de probleemoplosser verklaren hoe te om ruimte en configuratiekwesties met gegevensbestanden problemen op te lossen.

## Stap 1 - Identificeer de folder met een ruimtekwestie {#step-1}

+++**hebt u een `/tmp` kwestie die door een gebrek van ruimte wordt veroorzaakt?**

Dit kan worden aangegeven door een reeks symptomen, waaronder het feit dat de `/tmp` -montage vol is, is ingedrukt of niet in staat is om SSH in een knooppunt te plaatsen. U kunt fouten als _ook ervaren Geen ruimte verlaten op apparaat (28)_. Voor een lijst van fouten die het resultaat zijn van `/tmp` volledig zijn, herzie [&#x200B; /tmp zet volledig &#x200B;](/help/troubleshooting/miscellaneous/tmp-mount-full.md) op.

Of heeft u een `/data/mysql` -probleem dat wordt veroorzaakt door een gebrek aan ruimte? Dit kan ook door een verscheidenheid van symptomen met inbegrip van plaatsstroomonderbreking, klanten niet kunnen om producten aan kar toe te voegen, verbindingsmislukking aan gegevensbestand, en Galeria fouten zoals _SQLSTATE \ [08S01 \]: Communicatie verbindingsmislukking: 1047 WSREP_ worden vermeld. Voor een lijst van fouten die uit lage [!DNL MySQL] schijfruimte voortvloeien, verwijs naar [[!DNL MySQL]  schijfruimte is laag op Adobe Commerce op wolkeninfrastructuur &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-27806).

Als u onzeker bent als u een kwestie van de schijfruimte hebt en u een rekening van New Relic hebt, ga naar de [&#x200B; pagina van de Gastheren van de Infrastructuur van New Relic de controle &#x200B;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). Van daar, klik op het **lusje van de Opslag**, verander de **Grafiek toont** daling neer van 5 tot 20 resultaten, en kijk in de lijst voor hoog schijfgebruik in de Schijf Gebruikte % grafiek of de lijst. Voor meer gedetailleerde stappen, verwijs naar [ de Controle van de Infrastructuur van New Relic > het lusje van de Opslag ] https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Als u een van de hierboven beschreven symptomen heeft, controleert u de toestand van de inodes om te controleren of dit niet wordt veroorzaakt door problemen met het bestandsnummer. Dit doen stelt het volgende bevel in CLI/Terminal in werking:\
`df -ih`

Is IUse% > 90%?

a. JA - Dit wordt veroorzaakt door te veel bestanden. Herzie de stappen om dossiers veilig in [&#x200B; te verwijderen schrap veilig dossiers wanneer uit schijfruimte, Adobe Commerce op wolkeninfrastructuur &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26889). Ga aan [&#x200B; Stap 2 &#x200B;](#step-2) te werk nadat u deze stappen hebt voltooid. Als u meer ruimte wilt verzoeken, [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO. - Ruimte controleren. Voer `df -h | grep mysql` en vervolgens `df -h | grep tmp` uit in de CLI/Terminal om het gebruik van schijfruimte in de mappen `/tmp` en `/data/mysql` te controleren. Ga aan [&#x200B; Stap 3 &#x200B;](#step-3) te werk.

+++

## Stap 2 - Schijfruimte controleren {#step-2}

+++**gebruik van de schijfruimte van de Controle?**

Als u het aantal bestanden hebt verminderd, voert u `df -h | grep mysql` en vervolgens `df -h | grep tmp` in de CLI/Terminal uit om het gebruik van schijfruimte in `/tmp` en `/data/mysql` te controleren. Wordt meer dan 70% gebruikt voor `/tmp` of `/data/mysql`?

a. JA - ga aan [&#x200B; Stap 3 &#x200B;](#step-3) te werk.
b. NO - De vraag kan de beschikbare opslag uitputten. Hierdoor kan het knooppunt vastlopen, waarbij de query wordt gedood en de `tmp` -bestanden worden verwijderd. Onderzoek de output van `SHOW PROCESSLIST;` in [!DNL MySQL] CLI voor vragen die de oorzaak van het probleem kunnen zijn. [&#x200B; legt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor, die om meer ruimte verzoeken.

+++

## Stap 3 - Identificeer directory met hoog gebruik {#step-3}

+++**Welke folder heeft meer dan 70% gebruikt?**

Welke folder heeft meer dan 70% gebruikt? `/tmp` of `/data/mysql` ?

>[!NOTE]
>
>Standaard schrijft tmpdir naar `/tmp` . Als u wilt controleren of uw databaseconfiguratie nog steeds op deze standaard is, voert u de volgende opdracht in [!DNL MySQL] CLI uit: `SHOW VARIABLES LIKE "TMPDIR";` Als de databasetmpdir nog steeds naar `/tmp` schrijft, ziet u `/tmp` in de kolom Waarde.

a. `/tmp` - ga aan [&#x200B; Stap 4 &#x200B;](#step-4) te werk. \
b. `/data/mysql` - ga aan [&#x200B; Stap 5 &#x200B;](#step-5) te werk.

+++

## Stap 4 - los /tmp volledige onderstel problemen op {#step-4}

+++**los /tmp volledige opzetten** problemen op

[&#x200B; los /tmp zet vol voor Adobe Commerce &#x200B;](/help/troubleshooting/miscellaneous/tmp-mount-full.md) problemen op, scrol neer het artikel en probeer de oplossingen en beste praktijken. Voer vervolgens `df -h | grep mysql` en vervolgens `df -h | grep tmp` in de CLI/Terminal uit om het gebruik van schijfruimte in mappen `/tmp` en `/data/mysql` te controleren\
  &lt; 70% gebruikt?

>[!NOTE]
>
>De oplossingen in [&#x200B; lossen /tmp zet volledig voor Adobe Commerce &#x200B;](/help/troubleshooting/miscellaneous/tmp-mount-full.md) op worden ontworpen voor handelaren die niet de variabelen voor gegevensbestandtmpdir hebben veranderd, die door gebrek aan `/tmp` schrijft. Als u de tmpdir waarde hebt veranderd, zullen de instructies in [&#x200B; problemen /tmp koppelen volledig voor Adobe Commerce &#x200B;](/help/troubleshooting/miscellaneous/tmp-mount-full.md) niet helpen.

a. JA - U hebt de kwestie opgelost. \
b. NO - [&#x200B; legt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor, die om meer ruimte verzoeken.

+++

## Stap 5 - standaard controleren {#step-5}

+++**Controle gebrek**

Uw databaseconfiguratie bevindt zich mogelijk niet meer op de oorspronkelijke standaard. Zoek de tmpdir-configuratie van de database door deze uit te voeren in de [!DNL MySQL] CLI: `SELECT @@DATADIR;` . Als `/data/mysql/` wordt uitgevoerd, schrijft de database-tmpdir nu naar `/data/mysql/` . Probeer om ruimte in deze folder te verhogen door de stappen in [[!DNL MySQL]  schijfruimte te volgen is laag op Adobe Commerce op onze wolkeninfrastructuur &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-27806). Voer vervolgens `df -h | grep mysql` en vervolgens `df -h | grep tmp` in de CLI/Terminal uit om het gebruik van schijfruimte in `/data/mysql` en `/tmp` te controleren.\
  &lt; 70% gebruikt?

a. JA - U hebt de kwestie opgelost. \
b. NO - [&#x200B; legt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor, die om meer ruimte verzoeken.

+++

[&#x200B; terug naar Stap 1 &#x200B;](#step-1)

## Gerelateerde lezing

* [&#x200B; Beste praktijken voor het wijzigen van gegevensbestandlijsten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
