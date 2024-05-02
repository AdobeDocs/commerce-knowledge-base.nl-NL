---
title: 'ACSD-57003: De status van de bestelling wordt gewijzigd in *Complete* in plaats van te worden gewijzigd in *Processing*'
description: Pas de ACSD-57003-patch toe om het Adobe Commerce-probleem op te lossen waarbij de status van de bestelling verandert in *Complete* in plaats van te veranderen in *Processing*.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: c3c59185-c447-46fa-b404-6c4a4a300315
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-57003: statuswijzigingen van bestellingen naar *Voltooid* in plaats van over te schakelen op *Verwerking*

De ACSD-57003-patch verhelpt het probleem waarbij de orderstatus verandert in *Voltooid* in plaats van over te schakelen op *Verwerking*. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.46 is geïnstalleerd. De patch-id is ACSD-57003. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De orderstatus verandert in *Voltooid* in plaats van over te schakelen op *Verwerking* wanneer een bestelling gedeeltelijk wordt terugbetaald en gedeeltelijk wordt verzonden.

<u>Stappen om te reproduceren</u>:

1. Creeer een orde met twee configureerbare producten.
1. Factuur alle items.
1. Alleen het eerste object verzenden.
1. Een creditnota terugbetalen/maken voor alleen het verzonden object (*eerste object*).
1. Controleer de orderstatus.

<u>Verwachte resultaten</u>:

De status van de bestelling moet in de _Verwerking_ status.

<u>Werkelijke resultaten</u>:

Status van bestelling wijzigen in *Voltooid* nadat je een creditnota hebt gemaakt voor het gedeeltelijk verzonden object.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
