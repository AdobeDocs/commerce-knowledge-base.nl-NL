---
title: 'ACSD-48300: de terugkeer kan niet worden gecreeerd als configureerbaar product wordt verwijderd'
description: Pas de ACSD-48300-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de return niet kan worden gemaakt als het configureerbare product wordt verwijderd.
exl-id: 4abbc398-b341-4ff6-9483-9cf8f3dbbfbb
feature: Admin Workspace, Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-48300: de terugkeer kan niet worden gecreeerd als configureerbaar product wordt verwijderd

De ACSD-48300-patch verhelpt het probleem waarbij geen terugkeer kan worden gemaakt als het configureerbare product wordt verwijderd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 is geïnstalleerd. De patch-id is ACSD-48300. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De terugkeer kan niet worden gecreeerd als het configureerbare product wordt verwijderd.

<u>Stappen om te reproduceren</u>:

1. RMA inschakelen in de winkel op **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**.
1. Maak een configureerbaar product.
1. Maak in de winkel een account (en/of meld u aan).
1. Voeg een configureerbaar product aan de kar als eerste punt toe.
1. Voeg vervolgens een eenvoudig product toe.
1. Plaats de bestelling.
1. Verplaats de bestelling.
1. Verwijder nu alleen het configureerbare product (verwijder de onderliggende producten niet).
1. Ga in de winkel naar **[!UICONTROL My Orders]** en bekijk de volgorde.
1. Klikken op **[!UICONTROL Return]**.

<u>Verwachte resultaten</u>:

Admin kan punten terugkeren alhoewel het configureerbare product wordt geschrapt.

<u>Werkelijke resultaten</u>:

Er treedt een fout op bij het retourneren van items.

```
report.CRITICAL: Error: Call to a member function getShipmentType() on null in magento2ee/app/code/Magento/Rma/view/frontend/templates/return/create.phtml:52
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
