---
title: '"ACSD-52786: Catalogusregel *[!UICONTROL SKU is]* is van toepassing op alle producten die beginnen met de SKU'''
description: Pas de ACSD-52786-patch toe om het Adobe Commerce-probleem op te lossen waarbij de voorwaarde van de catalogusregel geldt *[!UICONTROL SKU is]* geldt voor alle producten die beginnen met de opgegeven SKU.
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786: Catalogusregel &quot;*[!UICONTROL SKU is]*&quot; is van toepassing op alle producten die beginnen met de SKU

Met de ACSD-52786-patch is het probleem verholpen waarbij de voorwaarde van de catalogusregel *[!UICONTROL SKU is]* van toepassing op alle producten die beginnen met de gegeven SKU. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-52786. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Voorwaarde van catalogusregel *[!UICONTROL SKU is]* van toepassing op alle producten die beginnen met de gegeven SKU.

<u>Stappen om te reproduceren</u>:

1. Maak twee producten, een met SKU &quot;24&quot; en een ander met SKU &quot;24-MB01&quot;.
1. Navigeren naar **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Pas de volgende voorwaarde toe:
   * *[!UICONTROL If ** ALLES **van deze voorwaarden** TRUE **]*: *[!UICONTROL SKU is 24]*
1. Stel een kortingsbedrag in in handelingen.
1. Klik op **[!UICONTROL Save and Apply]**.
1. Cachegeheugen leegmaken.
1. Ga naar de winkel en controleer de prijs van 24 MB01.

<u>Verwachte resultaten</u>:

De catalogusregel wordt toegepast slechts op één enkel product met SKU gelijk aan 24.

<u>Werkelijke resultaten</u>:

Voorwaarde van catalogusregel *[!UICONTROL SKU is]* van toepassing op alle producten die beginnen met de gegeven SKU.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
