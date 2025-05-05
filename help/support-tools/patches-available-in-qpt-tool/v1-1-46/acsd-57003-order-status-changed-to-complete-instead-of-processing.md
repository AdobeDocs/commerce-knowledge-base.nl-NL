---
title: 'ACSD-57003: de statuswijzigingen van bestellingen worden gewijzigd in *Complete* in plaats van te worden gewijzigd in *Processing*'
description: Pas de ACSD-57003-patch toe om het Adobe Commerce-probleem op te lossen waarbij de status van de bestelling verandert in *Complete* in plaats van te veranderen in *Processing*.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: c3c59185-c447-46fa-b404-6c4a4a300315
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-57003: De statusveranderingen van de orde in *Volledige* in plaats van het veranderen in *Verwerking*

ACSD-57003 herstelt de flard waar de ordestatus in *Volledige* in plaats van het veranderen in *Verwerking* verandert. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.46 wordt geïnstalleerd. De patch-id is ACSD-57003. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De ordestatus verandert in *Volledig* in plaats van het veranderen in *Verwerking* wanneer een orde gedeeltelijk wordt terugbetaald en gedeeltelijk verscheept.

<u> Stappen om </u> te reproduceren:

1. Creeer een orde met twee configureerbare producten.
1. Factuur alle items.
1. Alleen het eerste object verzenden.
1. Restitueer/creeer een creditnota voor slechts het verscheepte punt (*eerste punt*).
1. Controleer de orderstatus.

<u> Verwachte resultaten </u>:

De status van de orde zou in de _staat van de Verwerking_ moeten zijn.

<u> Ware resultaten </u>:

De statusveranderingen van de orde in *Volledige* na het creëren van een creditnota voor gedeeltelijk verscheept punt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
