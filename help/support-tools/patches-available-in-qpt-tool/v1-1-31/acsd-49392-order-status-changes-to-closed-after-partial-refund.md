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

De ACSD-49392-patch verhelpt het probleem waarbij de status van de bestelling verandert in gesloten na een gedeeltelijke terugbetaling voor een gebundeld product. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.31 is geïnstalleerd. De patch-id is ACSD-49392. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.3.7-p4 en 2.4.1 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van de bestelling verandert in gesloten na een gedeeltelijke terugbetaling voor een gebundeld product.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij Adobe Commerce en maak een gebundeld product of gebruik het bestaande gebundelde product.
1. Plaats een bestelling met dit gebundelde product met een hoeveelheid groter dan 1.
1. Ga naar beheerder en open de volgorde die u in stap 2 hebt gemaakt vanaf **[!UICONTROL Sales]** > **[!UICONTROL Order]** en maak een factuur. Bekijk de status van de order. Het wordt verwerkt.
1. Maak een gedeeltelijke creditnota (verbeter niet alle producten in de bundel).
1. Controleer de orderstatus.

<u>Verwachte resultaten</u>

Nadat u een gedeeltelijke creditnota voor het gebundelde product hebt gemaakt, wordt de status van de bestelling verwerkt.

<u>Werkelijke resultaten</u>

Na het maken van een gedeeltelijke creditnota voor het gebundelde product, is de ordestatus volledig.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
