---
title: 'ACSD-56760: Admin user is limited to a specific website and is unable to sort or add new products'
description: Pas de ACSD-56760-patch toe om het Adobe Commerce-probleem op te lossen waarbij de Admin-gebruiker die beperkt is tot een specifieke website en geen nieuwe producten in een categorie kan sorteren of toevoegen als de webwinkel een eigen hoofdcategorie heeft.
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760: Admin-gebruiker is beperkt tot een specifieke website en kan nieuwe producten niet sorteren of toevoegen

De ACSD-56760-patch verhelpt het probleem waarbij de Admin-gebruiker die beperkt is tot een specifieke website en geen nieuwe producten in een categorie kan sorteren of toevoegen als de webwinkel een eigen hoofdcategorie heeft. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.47 is geïnstalleerd. De patch-id is ACSD-56760. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De Admin-gebruiker die beperkt is tot een specifieke website en geen nieuwe producten binnen een categorie kan sorteren of toevoegen als de webwinkel een eigen hoofdcategorie heeft.

<u> Stappen om </u> te reproduceren:

1. Creeer *2* websites.
1. Creeer a **[!UICONTROL restricted admin user]** met toegang tot slechts *1* website.
1. Meld u aan als de **[!UICONTROL restricted admin user]** en probeer de productposities in een categorie te wijzigen.

*Geval 1*:

* *2* opslag.
* *2* wortelcategorieën, elke website die aan het wordt toegewezen is eigen categoriewortel.

*Geval 2*:

* *2* opslag.
* Slechts *1* wortelcategorie wordt toegewezen aan beide websites.

<u> Verwachte resultaten </u>:

* *Geval 1*: Beperkte admin zou producten binnen de beschikbare categorie moeten kunnen sorteren.
* *Geval 2*: Beperkte admin kan geen producten binnen de beschikbare categorie sorteren, omdat dit ook de beperkte opslag zal beïnvloeden.

<u> Ware resultaten </u>:

* *Geval 1*: Beperkte admin kan geen producten binnen de beschikbare categorie sorteren.
* *Geval 2*: Beperkte admin kan producten binnen de beschikbare categorie sorteren, die de beperkte opslag beïnvloedt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
