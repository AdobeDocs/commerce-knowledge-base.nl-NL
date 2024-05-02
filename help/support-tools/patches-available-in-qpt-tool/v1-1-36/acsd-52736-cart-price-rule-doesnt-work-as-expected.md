---
title: "ACSD-52736: [!UICONTROL Cart Price Rule] werkt niet zoals verwacht"
description: Pas de ACSD-52736-patch toe om het Adobe Commerce-probleem op te lossen waarbij een [!UICONTROL Cart Price Rule] dat de vereisten voor configureerbare producthoeveelheid omvat, werkt niet zoals verwacht.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] werkt niet zoals verwacht

De ACSD-52736-patch verhelpt het probleem waarbij een [!UICONTROL Cart Price Rule] dat de vereisten voor configureerbare producthoeveelheid omvat, werkt niet zoals verwacht. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 is geïnstalleerd. De patch-id is ACSD-52736. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

A [!UICONTROL Cart Price Rule] dat de vereisten voor configureerbare producthoeveelheid omvat werkt niet zoals verwacht.

<u>Stappen om te reproduceren</u>:

1. Een winkelwagentregel maken:
   * [!UICONTROL Apply] = Percentage van de korting op de productprijs
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Pas de regel alleen toe op de winkelwagentjes die aan de volgende voorwaarden voldoen: hoeveelheid in winkelwagentje is 1
2. Een product toevoegen met [!UICONTROL Qty] = 2, op de kar.
3. Controleer de prijzen van winkelwagentjes.

<u>Verwachte resultaten</u>:

De regel wordt niet toegepast omdat de hoeveelheid producten in de kar gelijk is aan *2*.

<u>Werkelijke resultaten</u>:

De korting wordt toegepast.

<u> Aanvullende stappen vereist na de installatie van de patch</u>:

Nadat u de pleister hebt aangebracht, bepaalt de kartonregel met behulp van *Aantal* moet worden verwijderd en opnieuw worden toegevoegd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
