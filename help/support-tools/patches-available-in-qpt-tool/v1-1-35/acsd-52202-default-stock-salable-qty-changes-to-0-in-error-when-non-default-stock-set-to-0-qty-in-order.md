---
title: 'ACSD-52202: De standaard verkochte hoeveelheid in voorraad verandert in 0 ten onrechte als de niet-standaard voorraad op 0 qty in volgorde is ingesteld.'
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

De ACSD-52202-patch verhelpt het probleem waarbij een standaard verkochte hoeveelheid (hoeveelheid) in voorraad verandert in 0 als de niet-standaard voorraad wordt ingesteld op 0 in een volgorde. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-52202. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De standaard verkochte hoeveelheid van de voorraad verandert in 0 ten onrechte wanneer de niet-standaardvoorraad wordt ingesteld op 0 in een volgorde.

<u>Stappen om te reproduceren</u>:

1. Aanmelden bij de [!DNL Admin].
1. Maken **website2**.
1. Aangepast maken **bron2**.
1. Aangepast maken **voorraad2**.
1. Wijs het **bron2** en **voorraad2** tot **website1** en de standaardbron en -voorraad voor de standaardwebsite.
1. Een eenvoudig product maken en toewijzen **kwik** = *10* voor de standaardbron en **kwik** = *1* voor de **bron2** bron.
1. Een bestelling plaatsen met **kwik** = *1* for **website2**.
1. Maak een factuur en een verzending.
1. Controleer het eenvoudige product **verkoopbare hoeveelheid**.

<u>Verwachte resultaten</u>:

De **verkoopbare hoeveelheid** = *10* for **bron2**.

<u>Werkelijke resultaten</u>:

De **verkoopbare hoeveelheid** = *0* voor beide bronnen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
