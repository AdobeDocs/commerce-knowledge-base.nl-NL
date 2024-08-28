---
title: '''ACSD-46938: Prestatieproblemen met DB-triggers tijdens ''setup:upgrade'''
description: Pas ACSD-46938 flard toe om de kwestie van Adobe Commerce te bevestigen waar het "opstelling:verbetering"bevel de indexeerwijze van programma verandert om te bewaren, veroorzakend significante prestatiesvertragingen.
feature: Upgrade
role: Admin, Developer
source-git-commit: cbd16ac7c6d6d7a4e3786880409475a10964c070
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-46938: Prestatieproblemen met DB-triggers tijdens `setup:upgrade`

De ACSD-46938-patch verhelpt het probleem waarbij de opdracht `setup:upgrade` de indexeermodus van een programma wijzigt om te besparen, wat aanzienlijke prestatievertragingen veroorzaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-46938. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Prestatieverslechtering tijdens DB activeert recreatie in `setup:upgrade` .

<u> Stappen om </u> te reproduceren:

1. Maak een grote catalogus met veel producten en categorieën.
1. Meld u aan bij de [!UICONTROL Admin] .
1. Stel alle indexen in op de modus [!UICONTROL Update By Schedule] .
1. Open een willekeurig product.
1. Werk het bij. Wijs bijvoorbeeld een nieuwe categorie toe.
1. Klik op [!UICONTROL Save].
1. Voer de opdrachten `bin/magento setup:upgrade` en `bin/magento cron:run` parallel uit.

<u> Verwachte resultaten </u>:

De uitvoeringstijd van de opdracht `bin/magento setup:upgrade` neemt aanzienlijk toe wanneer de opdracht `bin/magento cron:run` tegelijkertijd wordt uitgevoerd.

<u> Ware resultaten </u>:

De uitvoeringstijd van de opdracht neemt niet toe.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
