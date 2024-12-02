---
title: 'ACSD-54376: Uitzondering in winkelwagentje wanneer product uit [!UICONTROL shared catalog] wordt verwijderd'
description: Pas de ACSD-54376-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een uitzondering optreedt in het winkelwagentje wanneer een product uit de [!UICONTROL shared catalog] wordt verwijderd nadat het aan het winkelwagentje is toegevoegd.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: a1e5c084-532f-49e8-ab87-6674b44218e8
source-git-commit: 1cc565d5888e5a380c04879d9aced2c19e92c2e5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54376: Uitzondering in winkelwagentje wanneer product uit [!UICONTROL shared catalog] wordt verwijderd

De ACSD-54376-patch verhelpt het probleem dat zich een uitzondering voordoet in het winkelwagentje wanneer een product uit de [!UICONTROL shared catalog] wordt verwijderd nadat het aan het winkelwagentje is toegevoegd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 wordt geïnstalleerd. De patch-id is ACSD-54376. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een uitzondering op in het winkelwagentje wanneer een product uit de [!UICONTROL shared catalog] wordt verwijderd nadat het aan de winkelwagentje is toegevoegd.

<u> Stappen om </u> te reproduceren:

1. Adobe Commerce installeren met B2B.
1. Schakel [!UICONTROL shared catalog] in.
1. Maak een product en wijs dit toe aan de standaardwaarde [!UICONTROL shared catalog] .
1. Voeg een product uit de winkel toe aan de winkelwagentje.
1. Verwijder het product uit de [!UICONTROL shared catalog] .
1. Navigeer naar de uitcheckpagina met behulp van de mini-cart vervolgkeuzelijst.

<u> Verwachte resultaten </u>:

Uitzonderingen worden afgehandeld en niet aan u weergegeven.

<u> Ware resultaten </u>:

Een niet-afgehandelde uitzondering wordt weergegeven op de uitcheckpagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
