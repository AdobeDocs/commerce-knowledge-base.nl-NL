---
title: Weinig schijfruimte
description: In dit artikel worden oplossingen voorgesteld voor de situatie waarin er onvoldoende ruimte is in een bepaalde omgeving van Adobe Commerce op cloudinfrastructuur.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Weinig schijfruimte

In dit artikel worden oplossingen voorgesteld voor de situatie waarin er onvoldoende ruimte is in een bepaalde omgeving van Adobe Commerce op cloudinfrastructuur.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, alle [ gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

Er is onvoldoende schijfruimte op de schijf met beschrijfbare mappen. Één symptoom kan [ geplakte plaatsing ](/help/troubleshooting/deployment/deployment-stuck-with-unable-to-upload-the-application-to-the-remote-cluster-error.md) zijn.

Voer de volgende opdracht uit om het schijfgebruik te controleren:

```bash
df -h var/
```

## Oorzaak

De map `var` is meestal de map die veel ruimte kan innemen en eenvoudig kan worden schoongemaakt.

Adobe Commerce slaat alle logbestanden op in de map `var` . Er worden nieuwe logbestanden gemaakt en oude worden dagelijks gearchiveerd. Maar als het aantal gegenereerde fouten blijft toenemen, nemen logbestanden steeds meer ruimte in.

Aangepaste import-/exportbestanden worden ook opgeslagen in de map `var` en er wordt ruimte vrijgemaakt als het aantal bestanden toeneemt.

## Oplossing

Oplossingsopties:

* Controleer of u grote logbestanden hebt en ga na waarom deze groot zijn. Los dit probleem op door een grote hoeveelheid loguitvoer te genereren.
* Reinig de map `var` .
* Stel een uitsnijdtaak in om de grootte van de map `var` bij te houden en te opschonen.
* Wijs meer schijfruimte toe als u wat ongebruikte hebt. (Zie de onderstaande sectie voor informatie over hoe u kunt controleren wat uw limiet is voor ruimte.)
   * Voor het plan van de Aanzet, kunnen alle milieu&#39;s, en Pro de milieu&#39;s van de Integratie, u de schijfruimte toewijzen als u wat ongebruikt hebt, zoals die in [ wordt beschreven beheert schijfruimte: Het toewijzen van schijfruimte ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#application-disk-space).
   * Voor de milieu&#39;s van het Staging en van de Productie van het Pro Plan, contacteer steun om meer schijfruimte toe te wijzen als u wat ongebruikt hebt.
* Als u uw ruimtelimiet hebt bereikt en nog steeds weinig ruimte hebt, kunt u overwegen meer schijfruimte te kopen. Neem contact op met het accountteam van de Adobe voor meer informatie.

### Limiet schijfruimte controleren

Om te controleren hoeveel ruimte u voor elke Adobe Commerce hebt op de omgeving van de cloud-infrastructuur:

1. Login aan de [ Console van de Wolk ](https://console.adobecommerce.com).
1. Selecteer het desbetreffende project op het dashboard van **[!UICONTROL All projects]** . In de linkerhoek ziet u de beschikbaarheid van schijfruimte.

   ![ project_space.png ](/help/troubleshooting/miscellaneous/assets/project_space.png)
