---
title: 'ACSD-51819: meerdere bestellingen plaatsen met één aanhalings-id'
description: Pas de ACSD-51819-patch toe om het Adobe Commerce-probleem op te lossen, waarbij meerdere bestellingen via dezelfde aanhalings-id kunnen worden geplaatst.
feature: Orders, Checkout
role: Admin, Developer
exl-id: f217de21-2914-4b84-b596-e9e763669941
source-git-commit: 6fa7182a807147a00ad750966cd839ec18ffe0c7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51819: het plaatsen van veelvoudige orden met één enkele citaat identiteitskaart

De ACSD-51819-patch verhelpt het probleem waarbij meerdere bestellingen via dezelfde aanhalings-id kunnen worden geplaatst. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 is geïnstalleerd. De patch-id is ACSD-51819. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Meerdere bestellingen kunnen met dezelfde aanhalings-id worden geplaatst.

<u>Stappen om te reproduceren</u>:

1. Meld u aan als gebruiker.
1. Voeg items aan het winkelwagentje toe en ga door met het afrekenen.
1. Kies een betalingsmethode, maar klik niet op de knop **[!UICONTROL Place Order]** knop.
1. Meld u aan bij hetzelfde account in een andere browser.
1. Ga door met de kassa met dezelfde objecten zonder op de knop **[!UICONTROL Place Order]** knop.
1. Klik op de knop **[!UICONTROL Place Order]** in beide systemen tegelijk.
1. Valideer de orders die in beide browsers zijn geplaatst.

<u>Verwachte resultaten</u>:

Alleen de eerste bestelling die vanuit één browser is geplaatst, wordt verwerkt.

<u>Werkelijke resultaten</u>:

Bestellingen zijn in beide browsers geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
