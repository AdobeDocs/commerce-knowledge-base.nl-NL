---
title: 'ACSD-54885: Uitzondering tijdens uitchecken van meerdere adressen wanneer beheerders zich aanmelden als klant'
description: Pas de ACSD-54885-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een fout optreedt tijdens het uitchecken van meerdere adressen wanneer de beheerder de * gebruikt[!UICONTROL Login as Customer]* functionaliteit.
feature: Checkout
role: Admin, Developer
exl-id: 524ec96b-1465-4673-9fbe-1a9c086b7e87
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54885: Uitzondering tijdens uitchecken van meerdere adressen wanneer beheerders zich aanmelden als klant

De ACSD-54885-patch verhelpt het probleem waarbij een fout optreedt tijdens het uitchecken van meerdere adressen wanneer de beheerder de functie *[!UICONTROL Login as Customer]* functionaliteit. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 is geïnstalleerd. De patch-id is ACSD-54885. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een fout op tijdens het uitchecken van meerdere adressen wanneer de beheerder de functie *[!UICONTROL Login as Customer]* functionaliteit.

<u>Stappen om te reproduceren</u>:

1. Zorg ervoor dat *[!UICONTROL Login as Customer]* is ingeschakeld. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Maak een eenvoudig product.
1. Maak een nieuwe klantenaccount met een adres.
1. Ga naar de klantenaccount op de achtergrond:

   * Ga naar de **[!UICONTROL Account Information]** en -set *[!UICONTROL Allow remote shopping assistance]* = *Ja*.
   * Klik op **[!UICONTROL Login as Customer]**.

1. Het product aan de winkelwagentje toevoegen en doorgaan naar *[!UICONTROL Checkout with multiple addresses]*.
1. Werk het aantal producten bij.
1. Probeer terug te gaan naar het winkelwagentje.

<u>Verwachte resultaten</u>:

U kunt het winkelwagentje bijwerken en het uitchecken van meerdere adressen gebruiken.

<u>Werkelijke resultaten</u>:

Je krijgt de volgende fout wanneer je teruggaat naar het winkelwagentje.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
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
