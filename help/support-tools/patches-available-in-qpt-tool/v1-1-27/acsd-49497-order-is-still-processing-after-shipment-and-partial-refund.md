---
title: "ACSD-49497: bestelling die na verzending nog wordt verwerkt en gedeeltelijke terugbetaling"
description: Pas de ACSD-49497-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de status van de bestelling na verzending behouden blijft en een gedeeltelijke terugbetaling wordt toegepast.
exl-id: d195bcf4-bb8b-4373-8aad-a5b953b07443
feature: Admin Workspace, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-49497: nog te verwerken order na verzending en gedeeltelijke terugbetaling

De ACSD-49497-patch verhelpt het probleem dat de status van de bestelling blijft bestaan als verwerking na verzending en dat een gedeeltelijke terugbetaling wordt toegepast. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-49497. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van een nieuwe bestelling blijft in de *[!UICONTROL Processing]* ook na verzending vermelden en een gedeeltelijke terugbetaling toepassen.

<u>Stappen om te reproduceren</u>:

1. Maak een volgorde met meerdere items.
1. Van **[!UICONTROL Admin]**, maakt u een factuur voor de bestelling.
1. Van **[!UICONTROL Admin]**, maak een creditnota en restitueer een object slechts gedeeltelijk.
1. Van **[!UICONTROL Admin]**, vraag om verzending voor de resterende objecten in de bestelling.
1. Bekijk de status van de order.

<u>Verwachte resultaten</u>:

De status van de beschikking moet *[!UICONTROL Complete]*.

<u>Werkelijke resultaten</u>:

De status van de order blijft behouden *[!UICONTROL Processing]*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
