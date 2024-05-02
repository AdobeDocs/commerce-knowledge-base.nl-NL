---
title: "ACSD-52160: Resultaat van de productvalidering volgens de kartonprijsregel"
description: Pas de ACSD-52160-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het resultaat van de productvalidatie op basis van de regel voor de prijs van het winkelwagentje niet correct wordt geëvalueerd *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.
exl-id: a371c539-4440-4c84-baa4-774c32f66e41
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-52160: Resultaat van de productvalidatie volgens de kartonprijsregel wordt niet correct geëvalueerd

De ACSD-52160-patch verhelpt het probleem dat het resultaat van de productvalidatie ten opzichte van de kartonprijsregel niet correct wordt geëvalueerd op basis van de regelvoorwaarde *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 is geïnstalleerd. De patch-id is ACSD-52160. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het resultaat van de productvalidatie op basis van de regel van de winkelwagenprijs wordt niet correct beoordeeld op basis van de regelvoorwaarde *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.

<u>Stappen om te reproduceren</u>:

1. Maak twee producten die aan twee verschillende categorieën zijn toegewezen.
1. Een **[!UICONTROL Cart Price Rule]** met voorwaarden zoals:

   * **SKU 1** in de *[!UICONTROL FOUND]* parameter
   * **SKU 2** in de *[!UICONTROL NOT FOUND]* parameter

1. Voeg beide producten aan de kar toe.
1. Pas de couponcode toe.

<u>Verwachte resultaten</u>

De couponcode wordt niet toegepast omdat het winkelwagentje producten uit de categorie waarvoor beperkingen gelden, bevat.

<u>Werkelijke resultaten</u>

De couponcode wordt toegepast.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
