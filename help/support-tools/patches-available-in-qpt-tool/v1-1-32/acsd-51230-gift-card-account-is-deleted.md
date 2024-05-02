---
title: "ACSD-51230: Cadeaucreditcardaccount wordt verwijderd"
description: Pas de ACSD-51230-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de rekening van de cadeaukaart wordt verwijderd wanneer de gedeeltelijke terugbetaling van een eenvoudig product wordt verwerkt op basis van een bestelling.
exl-id: 4322a175-3641-468a-8a0f-fcbad90c758f
feature: Customer Service, Gift, Marketing Tools
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-51230: Cadeaukaartaccount is verwijderd

De ACSD-51230-patch verhelpt het probleem waarbij de rekening van de cadeaukaart wordt verwijderd wanneer de gedeeltelijke terugbetaling van een eenvoudig product wordt verwerkt op basis van een bestelling. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.32 is geïnstalleerd. De patch-id is ACSD-51230. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De rekening van de cadeaukaart wordt geschrapt wanneer de gedeeltelijke terugbetaling van een eenvoudig product van een orde wordt verwerkt.

<u>Stappen om te reproduceren</u>:

1. Een bestelling maken met een *Cadeaukaart* en *eenvoudig product* (bijvoorbeeld *add: SKU: GI000XX000XXX, SKU: PC046CP042076*) - (elke betaling en verzendmethode werkt.)
1. Factuur de bestelling.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Er wordt een account gemaakt voor de cadeaukaart.
1. Ga nu naar **[!UICONTROL Order]** en een **[!UICONTROL Credit Memo]**.
1. De hoeveelheid voor de *Cadeaukaart* naar 0 en bijwerken. Dit leidt tot een gedeeltelijke restitutie voor de *eenvoudig product*.
1. Klikken op **[!UICONTROL Refund]**.
1. Vernieuw nu de **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Het nieuwe account wordt verwijderd.

<u>Verwachte resultaten</u>

De rekening van de cadeaukaart is beschikbaar voor gebruik omdat de terugbetaling niet is gemaakt voor de cadeaukaart.

<u>Werkelijke resultaten</u>

Het kaartenaccount wordt verwijderd en de cadeaukaart wordt niet terugbetaald.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
