---
title: "ACSD-47004: BTW niet van toepassing op factuuradres zonder BTW-identificatienummer"
description: Pas de ACSD-47004-patch toe om het Adobe Commerce-probleem op te lossen dat BTW niet wordt geheven op een factuuradres zonder BTW-identificatienummer.
exl-id: 04706219-be1d-4d9a-a8bf-f5c24b45076d
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---

# ACSD-47004: BTW niet van toepassing op factuuradres zonder BTW-identificatienummer

Met de ACSD-47004-patch is het probleem opgelost dat btw niet wordt toegepast op een factuuradres zonder BTW-identificatienummer. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)  1.1.24 is geïnstalleerd. De patch-id is ACSD-47004. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

BTW wordt niet toegepast op een factuuradres zonder BTW-identificatienummer.

<u>Stappen om te reproduceren</u>:

1. Open de [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** en stelt de **[!UICONTROL Enable Automatic Assignment to Customer Group]** tot *[!UICONTROL Yes]*.
1. Stel verschillende groepen in voor BTW-ID-validaties. Bijvoorbeeld:
   ![BTW-ID-validaties](/help/support-tools/patches-available-in-qpt-tool/assets/vat-id-validations.png)
1. Registreer een nieuwe klant.
1. Voeg een nieuw standaardadres zonder BTW toe. Bijvoorbeeld:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Controleren of de groep van de klant behouden blijft [!UICONTROL General].
1. Bewerk dit adres en voeg een geldig BTW-nummer toe:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Zorg ervoor dat de groep van de klant is veranderd in [!UICONTROL Retailer].
1. Bewerk het adres en verwijder het BTW-nummer:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>Verwachte resultaten</u>:

De klantengroep wordt veranderd in het gebrek [!UICONTROL General] automatisch groeperen.

<u>Werkelijke resultaten</u>:

De klantengroep wordt niet gewijzigd in de standaardgroep [!UICONTROL General] automatisch groeperen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
