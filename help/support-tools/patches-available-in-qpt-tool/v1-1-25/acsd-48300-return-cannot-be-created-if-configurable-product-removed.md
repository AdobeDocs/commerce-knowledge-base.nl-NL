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

De ACSD-48300-patch verhelpt het probleem waarbij geen terugkeer kan worden gemaakt als het configureerbare product wordt verwijderd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-48300. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De terugkeer kan niet worden gecreeerd als het configureerbare product wordt verwijderd.

<u> Stappen om </u> te reproduceren:

1. Schakel RMA in de winkel in op **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]** .
1. Maak een configureerbaar product.
1. Maak in de winkel een account (en/of meld u aan).
1. Voeg een configureerbaar product aan de kar als eerste punt toe.
1. Voeg vervolgens een eenvoudig product toe.
1. Plaats de bestelling.
1. Verplaats de bestelling.
1. Verwijder nu alleen het configureerbare product (verwijder de onderliggende producten niet).
1. Ga in de winkel naar **[!UICONTROL My Orders]** en bekijk de volgorde.
1. Klik op **[!UICONTROL Return]** .

<u> Verwachte resultaten </u>:

Admin kan punten terugkeren alhoewel het configureerbare product wordt geschrapt.

<u> Ware resultaten </u>:

Er treedt een fout op bij het retourneren van items.

```
report.CRITICAL: Error: Call to a member function getShipmentType() on null in magento2ee/app/code/Magento/Rma/view/frontend/templates/return/create.phtml:52
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
