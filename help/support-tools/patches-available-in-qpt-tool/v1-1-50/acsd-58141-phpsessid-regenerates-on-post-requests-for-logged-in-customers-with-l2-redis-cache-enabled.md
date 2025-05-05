---
title: 'ACSD-58141: PHPSESSID regenereert op de verzoeken van de POST voor geregistreerde klanten met L2 toegelaten geheime voorgeheugen Redis'
description: Pas ACSD-58141 flard toe om de kwestie van Adobe Commerce te bevestigen waar &grave; PHPSESSID &grave; op de verzoeken van de POST op het gebied van de Storefront voor een het programma geopende klant met L2 Redis toegelaten geheime voorgeheugen regenereert, en de klant wordt bijgewerkt van Admin.
feature: Customers, Cache
role: Admin, Developer
exl-id: 72ae2ed4-bbac-472b-b257-3234f86000f4
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-58141: PHPSESSID regenereert op [!DNL POST] verzoeken voor aangemelde klanten als het L2 Redis geheime voorgeheugen wordt toegelaten

De ACSD-58141-patch verhelpt het probleem waarbij `PHPSESSID` opnieuw wordt gegenereerd op [!DNL POST] -aanvragen voor een aangemelde klant als de L2 Redis-cache is ingeschakeld, en de klant wordt bijgewerkt vanuit Admin. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-58141. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce en de versies van de Magento Open Source:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`PHPSESSID` wordt opnieuw gegenereerd op [!DNL POST] -aanvragen voor een aangemelde klant waarvoor de L2 Redis-cache is ingeschakeld.

<u> Eerste vereisten </u>

De omgeving moet worden geconfigureerd met Redis met ten minste drie knooppunten.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product.
1. Creeer een klant en login aan de Storefront.
1. Controleer de waarde van `PHPSESSID` .
1. Verzend enkele [!DNL POST] -aanvragen (bijv. product aan winkelwagentje toevoegen) en controleer of `PHPSESSID` hetzelfde blijft).
1. Meld u aan bij het deelvenster **[!UICONTROL Admin]** en wijzig de middelste naam van de klant.
1. Als de middelste naam is opgeslagen, wijzigt u deze en slaat u deze een paar keer opnieuw op.
1. Verzend een [!DNL POST] request in de winkel. `PHPSESSID` had moeten zijn bijgewerkt.
1. Stuur in de winkel nog een [!DNL POST] aanvraag en controleer `PHPSESSID` .
1. Herhaal de vorige stap een paar keer.

<u> Verwachte resultaten </u>

`PHPSESSID` wordt slechts eenmaal opnieuw gegenereerd nadat de klantgegevens zijn gewijzigd.

<u> Ware resultaten </u>:

`PHPSESSID` wordt telkens opnieuw gegenereerd wanneer de [!DNL POST] -aanvragen worden verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
