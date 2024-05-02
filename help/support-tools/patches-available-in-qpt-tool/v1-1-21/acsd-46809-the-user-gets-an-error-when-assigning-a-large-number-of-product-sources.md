---
title: 'ACSD-46809: De gebruiker krijgt een fout wanneer hij een groot aantal productbronnen toewijst'
description: Pas de ACSD-46809-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de gebruiker een fout krijgt bij het toewijzen van een groot aantal productbronnen.
exl-id: c67d7981-37fe-433a-b818-56a5b391082d
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-46809: De gebruiker krijgt een fout wanneer het toewijzen van een groot aantal productbronnen

De ACSD-46809-patch verhelpt het probleem waarbij de gebruiker een fout krijgt bij het toewijzen van een groot aantal productbronnen. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 is geïnstalleerd. De patch-id is ACSD-46809. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker krijgt een fout wanneer het toewijzen van een groot aantal productbronnen.

<u>Stappen om te reproduceren</u>:

1. Maak meer dan 200 aangepaste bronnen.
1. Ga naar Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Bewerk een product.
1. Wijs tegelijkertijd 200 bronnen aan dit product toe.

<u>Verwachte resultaten</u>:

Er worden 200 bronnen zonder fouten aan het product toegewezen

<u>Werkelijke resultaten</u>:

*Er is iets misgegaan* Er wordt een fout weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
