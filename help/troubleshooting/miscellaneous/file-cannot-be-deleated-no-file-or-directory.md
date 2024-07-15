---
title: "Het bestand kan niet worden verwijderd. Waarschuwing! ontkoppelen: Geen dergelijk dossier of folderfout van  [!DNL Admin]"
description: Dit artikel biedt een oplossing voor het probleem waarbij een fout *Het bestand kan niet worden verwijderd. Waarschuwing!ontkoppel geen dergelijk dossier of folderfout* van  [!DNL Admin]  wanneer u a  [!DNL Javascript/CSS]  uitlijnt.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *het dossier kan niet worden geschrapt. Waarschuwing!unlink: bestands- of mapfout is niet aanwezig* in het [!DNL Admin]

Dit artikel verstrekt een oplossing aan de kwestie waar u een fout *ziet het dossier kan niet worden geschrapt. Waarschuwing!ontkoppelen: geen bestands- of mapfout* van [!DNL Commerce Admin] wanneer u een [!DNL JavaScript/CSS] flush-bewerking uitvoert.

## Betrokken producten en versies

* Adobe Commerce 2.4.0 - 2.4.6, alle plaatsingsmethodes

## Probleem

Er treedt een fout op wanneer u een [!DNL JS/CSS] flush uitvoert:

*&quot;/app/pub/static/_cache/merge/.nfsa42d0e64799fd100000001b&quot;dossier kan niet worden geschrapt. Waarschuwing!unlink(/app/pub/static/_cache/merge/.nfsa42d0e64799fd100000001b): Geen dergelijk bestand of deze map*

Of: u ziet de bovenstaande fout in [!DNL Admin] en/of een vergelijkbare fout in [!DNL New Relic] of in de implementatielogboeken.

Of: U kunt geen toegang krijgen tot Geavanceerde rapportage en de taak Analytics_collect_data kan niet worden uitgevoerd als gevolg van deze fout:

*&quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0&quot;dossier kan niet worden geschrapt. Waarschuwing!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0): Geen dergelijk bestand of deze map*

<u> Stappen om te reproduceren:</u>

Methode 1:

1. Meld u aan bij de [!DNL Admin] .
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Cache Management]** .
1. Klik op **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]** .

Methode 2:

1. Meld u aan bij de [!DNL Admin] .
1. Ga naar **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** .
1. Breng wijzigingen aan in de [!UICONTROL Base URL] of [!UICONTROL Base URL (Secure)] .
1. Klik op **[!UICONTROL Save Config]** .

## Oplossing

Als u zich op Adobe Commerce op de Cloud-infrastructuur bevindt en [!DNL magento/magento-cloud-patches] 1.0.22 met de patch hebt geïnstalleerd, hoeft u ACSD-50165 niet afzonderlijk te installeren.

Adobe Commerce op de infrastructuur van de Wolk: De Patches van de Wolk van de Verbetering voor Commerce aan 1.0.22 (**of nieuwere**) die deze moeilijke situatie bevat: [ de Patches van de Wolk voor Commerce ](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce op-gebouw: Pas ACSD-50165 toe gebruikend [ Hulpmiddelen van de Patches van de Kwaliteit > Gebruik ](/docs/commerce-operations/tools/quality-patches-tool/usage.html). ACSD-50165 flard komt met [!DNL QPT] [ v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## Gerelateerde lezing

* [[!DNL Quality Patches Tool]  > Opmerkingen bij de release ](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) in de handleiding voor Commerce-gereedschappen.
* [[!DNL Quality Patches Tool]: zoek naar patches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de handleiding voor Commerce Tools.
