---
title: '"ACSD-47232: coupon wordt niet toegepast wanneer [!UICONTROL Same as Billing Address] is ingeschakeld.'
description: Pas de ACSD-47232-patch toe om het Adobe Commerce-probleem op te lossen waarbij geen coupon wordt gebruikt wanneer [!UICONTROL Same as Billing Address] is ingeschakeld.
exl-id: 29b95a0b-8792-4830-a1e5-ce977f8453ec
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232: coupon wordt niet toegepast wanneer [!UICONTROL Same as Billing Address] is ingeschakeld

De ACSD-47232-patch corrigeert de kwestie waar de coupon niet wordt gebruikt wanneer **[!UICONTROL Same as Billing Address]** is ingeschakeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 is geïnstalleerd. De patch-id is ACSD-47232. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Coupon wordt niet toegepast wanneer **[!UICONTROL Same as Billing Address]** is ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Adobe Commerce installeren.
1. Een eenvoudig product maken met gewicht = *8*.
1. Maak een nieuwe klant met standaardfacturering en standaardverzendadres.
1. Maak een regel voor de winkelprijs met een coupon.
   * In **[!UICONTROL Conditions]** secties toevoegen *Totaal gewicht gelijk aan of groter dan 5*
1. Probeer een nieuwe volgorde te maken in de [!UICONTROL Commerce] Admin.
   * Gebruik de klant die u zojuist hebt gemaakt
   * Een product toevoegen
   * Probeer de coupon toe te passen

<u>Verwachte resultaten</u>:

Coupon wordt toegepast.

<u>Werkelijke resultaten</u>:

Er treedt een fout op die lijkt op het volgende: *De 123-couponcode is niet geldig. Controleer de code en probeer het opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
