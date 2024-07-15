---
title: "ACSD-49392: Wijzigingen in de status van bestelling die na gedeeltelijke terugbetaling worden gesloten"
description: Pas de ACSD-49392-patch toe om het Adobe Commerce-probleem op te lossen waarbij de status van de order verandert in gesloten na een gedeeltelijke terugbetaling voor een gebundeld product.
exl-id: fca6f502-e224-4444-b0d0-f823853c9458
feature: Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-49392: Wijzigingen in de status van bestellingen die na gedeeltelijke terugbetaling worden gesloten

De ACSD-49392-patch verhelpt het probleem waarbij de status van de bestelling verandert in gesloten na een gedeeltelijke terugbetaling voor een gebundeld product. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.31 wordt geïnstalleerd. De patch-id is ACSD-49392. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.3.7-p4 en 2.4.1 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van de bestelling verandert in gesloten na een gedeeltelijke terugbetaling voor een gebundeld product.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij Adobe Commerce en maak een gebundeld product of gebruik het bestaande gebundelde product.
1. Plaats een bestelling met dit gebundelde product met een hoeveelheid groter dan 1.
1. Ga naar Beheer, open de volgorde die u in stap 2 hebt gemaakt via **[!UICONTROL Sales]** > **[!UICONTROL Order]** en maak een factuur. Bekijk de status van de order. Het wordt verwerkt.
1. Maak een gedeeltelijke creditnota (verbeter niet alle producten in de bundel).
1. Controleer de orderstatus.

<u> Verwachte resultaten </u>

Nadat u een gedeeltelijke creditnota voor het gebundelde product hebt gemaakt, wordt de status van de bestelling verwerkt.

<u> Ware resultaten </u>

Na het maken van een gedeeltelijke creditnota voor het gebundelde product, is de ordestatus volledig.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
