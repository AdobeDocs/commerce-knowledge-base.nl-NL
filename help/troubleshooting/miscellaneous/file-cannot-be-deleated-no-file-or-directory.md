---
title: "Het bestand kan niet worden verwijderd. Waarschuwing! ontkoppelen: geen bestands- of mapfout in de map [!DNL Admin]"
description: Dit artikel biedt een oplossing voor het probleem waarbij een fout *Het bestand kan niet worden verwijderd. Waarschuwing!Ontkoppel dergelijke bestand- of mapfout* niet via de [!DNL Admin] wanneer u een [!DNL Javascript/CSS] spoelen.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *Het bestand kan niet worden verwijderd. Waarschuwing!ontkoppelen: bestands- of mapfout bestaat niet* van de [!DNL Admin]

Dit artikel biedt een oplossing voor het probleem waarbij een fout optreedt *Het bestand kan niet worden verwijderd. Waarschuwing!ontkoppelen: bestands- of mapfout bestaat niet* van de [!DNL Commerce Admin] wanneer u een [!DNL JavaScript/CSS] spoelen.

## Betrokken producten en versies

* Adobe Commerce 2.4.0 - 2.4.6, alle plaatsingsmethodes

## Probleem

Er treedt een fout op wanneer u een [!DNL JS/CSS] uitspoelen:

*Het bestand &quot;/app/pub/static/_cache/merge/.nfsa42d0e64799fd100000001b&quot; kan niet worden verwijderd. Waarschuwing!unlink(/app/pub/static/_cache/merge/.nfsa42d0e64799fd100000001b): geen dergelijk bestand of map*

Of: u ziet de bovenstaande fout in het dialoogvenster [!DNL Admin]en/of een soortgelijke fout in [!DNL New Relic] of in de plaatsingslogboeken.

Of: U kunt geen toegang krijgen tot Geavanceerde rapportage en de taak Analytics_collect_data kan niet worden uitgevoerd als gevolg van deze fout:

*Het bestand &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0&quot; kan niet worden verwijderd. Waarschuwing!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0): geen dergelijk bestand of deze map*

<u>Stappen om te reproduceren:</u>

Methode 1:

1. Aanmelden bij de [!DNL Admin].
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Klikken **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

Methode 2:

1. Aanmelden bij de [!DNL Admin].
1. Ga naar **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Breng wijzigingen aan in de [!UICONTROL Base URL] of [!UICONTROL Base URL (Secure)].
1. Klikken op **[!UICONTROL Save Config]**.

## Oplossing

Als u zich op Adobe Commerce op Cloud-infrastructuur bevindt en [!DNL magento/magento-cloud-patches] 1.0.22 geïnstalleerd, inclusief de patch, hoeft u ACSD-50165 niet afzonderlijk te installeren.

Adobe Commerce on Cloud-infrastructuur: Cloud-patches voor Commerce upgraden naar 1.0.22 (**of nieuwer**) met deze correctie: [Cloud-patches voor handel](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce op locatie: ACSD-50165 toepassen met [Quality Patches Tools > Usage](/docs/commerce-operations/tools/quality-patches-tool/usage.html). De ACSD-50165-patch wordt meegeleverd [!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## Gerelateerde lezing

* [[!DNL Quality Patches Tool] > Opmerkingen bij de release](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) in de handleiding voor Commerce Tools.
* [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de handleiding voor Commerce Tools.
