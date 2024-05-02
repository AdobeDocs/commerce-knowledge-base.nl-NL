---
title: 'ACSD-48857: Kan wijzigingen niet opslaan na bewerking met [!DNL Page Builder]'
description: Pas de ACSD-48857-patch toe om het Adobe Commerce-probleem op te lossen waarbij de gebruiker na het bewerken geen wijzigingen kan opslaan [!DNL Page Builder].
exl-id: c95b354d-8954-4e9c-9e92-8a64f62f0a68
feature: Admin Workspace, CMS, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-48857: Kan wijzigingen niet opslaan na bewerking met [!DNL Page Builder]

De ACSD-48857-patch verhelpt het probleem waarbij de gebruiker na het bewerken met [!DNL Page Builder]. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 is geïnstalleerd. De patch-id is ACSD-48857. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruiker kan wijzigingen niet opslaan na bewerking met [!DNL Page Builder].

<u>Stappen om te reproduceren</u>

1. Meld u aan bij de beheerwebsite.
1. Navigeren naar **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** om een lege CMS-pagina te maken.
1. Voer dit SQL-script uit om het volgende in te stellen **[!UICONTROL Content]** veldwaarde:

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Terug naar **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** in Admin.
1. Bewerk de pagina.
1. Ga naar de **[!UICONTROL Content]** tab.
1. Klik op **[!UICONTROL Save]**.

<u>Verwachte resultaten</u>

ontsmetten met HTML-inhoud is geïmplementeerd. Hierdoor wordt [!DNL Page Builder] gereserveerde HTML-kenmerken in inhoud die wordt gegenereerd door de teksteditor.

<u>Werkelijke resultaten</u>

De pagina blijft niet opgeslagen en de lader blijft draaien. In de console, wordt de volgende fout geproduceerd:

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
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
