---
title: 'ACSD-56635: Geïmporteerde klanten worden gedupliceerd wanneer het delen van accounts wordt ingesteld op [!DNL Global]'
description: Pas de ACSD-56635-patch toe om het Adobe Commerce-probleem op te lossen waarbij de geïmporteerde klant hetzelfde e-mailadres heeft wanneer het importeren wordt gebruikt en het delen van account is ingesteld op [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
source-git-commit: 86d752c9c2791ef19960876afafe24fefe5d29ed
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635: Geïmporteerde klanten worden gedupliceerd met hetzelfde e-mailadres wanneer het delen van hun account is ingesteld op [!DNL Global]

De ACSD-56635-patch verhelpt het probleem waarbij de geïmporteerde klant wordt gedupliceerd met hetzelfde e-mailadres wanneer het importeren wordt gebruikt en account delen is ingesteld op [!DNL Global]. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 is geïnstalleerd. De patch-id is ACSD-56635. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Geïmporteerde klanten worden met hetzelfde e-mailadres gedupliceerd wanneer het delen van een account is ingesteld op [!DNL Global].

<u>Stappen om te reproduceren</u>:

1. Onder de Adobe Commerce (2.4-ontwikkeling b2b) **[!UICONTROL Admin]**, toegang **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. Stel de *[!UICONTROL Share Customer Accounts]* instellen op *[!DNL Global]*.
1. Meerdere websites en winkels maken:

   * ws1 > s11, s12 > sw111, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Een nieuwe klant maken onder de *hoofdwebsite* van beheerder met e-mailadres gebruikt als <adb@yormail.com>.
1. Onder **[!UICONTROL Admin]**, navigeer naar **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. Selecteren **[!UICONTROL Customer Entity Type]** als *[!UICONTROL Customers Main File]*.
1. Hetzelfde e-mailadres gebruiken als <adb@yormail.com> op een andere website, bijvoorbeeld ws1. Raadpleeg het voorbeeld CSV-bestand customer.csv hieronder.
1. Voer de importbewerking uit om te zien welke nieuwe gebruiker is gemaakt onder het dialoogvenster *ws1* website met hetzelfde e-mailadres.

content customer.csv:

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>Verwachte resultaten</u>:

De geïmporteerde klant met hetzelfde e-mailadres wordt bijgewerkt in plaats van te worden gedupliceerd.

<u>Werkelijke resultaten</u>:

Dubbele klanten worden met hetzelfde e-mailadres gemaakt wanneer ze de klant importeren gebruiken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
