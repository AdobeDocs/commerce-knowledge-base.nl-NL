---
title: 'ACSD-52202: De standaard verkochte hoeveelheid van de voorraad verandert in 0 ten onrechte als de niet-standaard voorraad op 0 qty wordt ingesteld'
description: Pas de ACSD-52202-patch toe om het Adobe Commerce-probleem op te lossen waarbij een standaardhoeveelheid die in voorraad kan worden verkocht, verandert in 0 als de niet-standaardvoorraad is ingesteld op 0 in een bestelling.
feature: Inventory, Products
role: Admin
exl-id: 8a3b5da4-cf16-41c8-b2d5-b740d638c745
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52202: De standaardhoeveelheid die in voorraad kan worden verkocht, verandert ten onrechte in 0 wanneer de niet-standaardvoorraad op 0 staat in een volgorde

De ACSD-52202-patch verhelpt het probleem waarbij een standaard verkochte hoeveelheid (hoeveelheid) in voorraad verandert in 0 als de niet-standaard voorraad wordt ingesteld op 0 in een volgorde. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-52202. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De standaard verkochte hoeveelheid van de voorraad verandert in 0 ten onrechte wanneer de niet-standaardvoorraad wordt ingesteld op 0 in een volgorde.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de [!DNL Admin] .
1. Creeer **website2**.
1. Creeer douane **source2**.
1. Creeer douane **stock2**.
1. Wijs **source2** en **stock2** aan **website1** en de standaardbron en de voorraad aan de standaardwebsite toe.
1. Creeer een eenvoudig product en wijs **hoeveelheid** toe = *10* voor standaardbron en **qty** = *1* voor de **bron2** bron.
1. Plaats een orde met **qty** = *1* voor **website2**.
1. Maak een factuur en een verzending.
1. Controleer het eenvoudige product **verkoopbare aantal**.

<u> Verwachte resultaten </u>:

De **verkoopbare hoeveelheid** = *10* voor **source2**.

<u> Ware resultaten </u>:

De **verkoopbare hoeveelheid** = *0* voor beide bronnen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
