---
title: 'ACSD-49839: De gedeelde catalogusprijzen en -structuur genereren een fout'
description: Pas de ACSD-49839-patch toe om het Adobe Commerce-probleem op te lossen waarbij de prijs en structuur van de gedeelde catalogus een fout in de beheerder veroorzaken wanneer producten enkele of dubbele aanhalingstekens in SKU hebben.
exl-id: 4c477ae8-602b-452e-83f0-b72a29547ef9
feature: Admin Workspace, Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49839: De gedeelde catalogusprijzen en -structuur genereren een fout

De ACSD-49839-patch verhelpt het probleem waarbij de gedeelde catalogusprijs en -structuur een fout veroorzaken in de beheerder wanneer producten enkele of dubbele aanhalingstekens in SKU hebben. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-49839. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gedeelde catalogusprijs en de structuur werpen een fout in admin wanneer de producten enige of dubbele citaten in SKU hebben.

<u> Stappen om </u> te reproduceren:

1. Stel enkele SKU&#39;s van het product in met een speciaal teken, bijvoorbeeld dubbele aanhalingstekens, zoals:
   *[Product &quot;12, Product &quot;14, Product &quot;15]*.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Add Shared Catalog]** (bijvoorbeeld, *[Test Gedeelde Catalogus]*).
1. Wijs alles toe **[!UICONTROL Products and Categories]** > **[!UICONTROL Generate Catalog]** > **[!UICONTROL Save]** .
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Test Shared Catalog]** > **[!UICONTROL Action]** > **[!UICONTROL Set Pricing and Structure]** .
1. Markeer *[!UICONTROL Root Catalog]* om alle categorieën en producten te selecteren.
1. Bekijk de AJAX verzoeken in het netwerkpaneel.

<u> Verwachte resultaten </u>:

De gedeelde catalogusprijs en de structuur werpen geen fout in admin wanneer de producten enige of dubbele citaten in SKU hebben.

<u> Ware resultaten </u>:

De gedeelde catalogusprijs en de structuur werpen een fout in admin wanneer de producten enige of dubbele citaten in SKU hebben.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
