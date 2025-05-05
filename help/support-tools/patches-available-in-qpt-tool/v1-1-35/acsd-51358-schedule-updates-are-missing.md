---
title: 'ACSD-51358: planningupdates ontbreken'
description: Pas de ACSD-51358-patch toe om het Adobe Commerce-probleem op te lossen waarbij de wijzigingen in de geplande update zonder einddatum ertoe leiden dat andere geplande updates op dezelfde entiteit worden verwijderd.
feature: Staging
role: Admin, Developer
exl-id: 8bc4c505-9cf2-4c33-93a1-4b4d7d0dfc15
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51358: planningupdates ontbreken

De ACSD-51358-patch verhelpt het probleem waarbij de wijzigingen in de geplande update zonder einddatum ertoe leiden dat andere geplande updates voor dezelfde entiteit worden verwijderd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-51358. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De wijzigingen in de geplande update zonder einddatum leiden tot het verwijderen van andere geplande updates voor dezelfde entiteit.

<u> Stappen om </u> te reproduceren:

1. Creeer a **[!UICONTROL scheduled update]** zonder de einddatum (*update 1*).
1. Creeer nieuw **[!UICONTROL scheduled update]** met zelfde begindatum zoals eerste update, maar voeg de volgende dag, en de einddatum toe (*update 2*).
1. Bewerk **[!UICONTROL scheduled update]** gecreeerd op stap 1 (*update 1*) en sparen veranderingen.

<u> Verwachte resultaten </u>

(*update 2*) zou in de **[!UICONTROL schedule update]** lijst moeten blijven wanneer (*update 1*) wordt uitgegeven.

<u> Ware resultaten </u>

(*update 2*) werd verwijderd uit de **[!UICONTROL schedule update]** lijst wanneer (*update 1*) wordt uitgegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL>) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL>) in de [!DNL Quality Patches Tool] gids.
