---
title: 'ACSD-56635: Geïmporteerde klanten worden gedupliceerd wanneer het delen van accounts is ingesteld op  [!DNL Global]'
description: Pas de ACSD-56635-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de geïmporteerde klant hetzelfde e-mailadres krijgt wanneer het importeren wordt gebruikt en account delen is ingesteld op  [!DNL Global] .
feature: Customers, Attributes
role: Admin, Developer
exl-id: abd542a1-6764-4385-97a6-b46015363b42
source-git-commit: 880fc679afc853b514fddda56e570fe1a279a3d9
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635: Geïmporteerde klanten worden gedupliceerd met hetzelfde e-mailadres wanneer het delen van een account is ingesteld op [!DNL Global]

De ACSD-56635-patch verhelpt het probleem waarbij de geïmporteerde klant wordt gedupliceerd met hetzelfde e-mailadres wanneer het importeren wordt gebruikt en account delen is ingesteld op [!DNL Global] . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-56635. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Geïmporteerde klanten worden met hetzelfde e-mailadres gedupliceerd wanneer het delen van een account is ingesteld op [!DNL Global] .

<u> Stappen om </u> te reproduceren:

1. Open **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** onder de Adobe Commerce (2.4-functie voor b2b) **[!UICONTROL Admin]** .
1. Stel de instelling *[!UICONTROL Share Customer Accounts]* in op *[!DNL Global]* .
1. Meerdere websites en winkels maken:

   * ws1 > s11, s12 > sw111, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Creeer een nieuwe klant onder de *belangrijkste website* van admin met e-mailadres dat als <adb@yormail.com> wordt gebruikt.
1. Navigeer onder **[!UICONTROL Admin]** naar **[!UICONTROL System]** > **[!UICONTROL Import]** .
1. Selecteer **[!UICONTROL Customer Entity Type]** als *[!UICONTROL Customers Main File]* .
1. Gebruik hetzelfde e-mailadres als <adb@yormail.com> op een andere website, bijvoorbeeld ws1. Raadpleeg het voorbeeld CSV-bestand customer.csv hieronder.
1. Voltooi de invoer om de nieuwe gebruiker te zien die onder de *wordt gecreeerd ws1* website met het zelfde e-mailadres.

content customer.csv:

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u> Verwachte Resultaten </u>:

De geïmporteerde klant met hetzelfde e-mailadres wordt bijgewerkt in plaats van te worden gedupliceerd.

<u> Ware Resultaten </u>:

Dubbele klanten worden met hetzelfde e-mailadres gemaakt wanneer ze de klant importeren gebruiken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
