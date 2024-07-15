---
title: 'ACSD-47803: configureerbare productstalen die buiten de voorraad worden weergegeven als beschikbaar'
description: Pas de ACSD-47803-patch toe om het Adobe Commerce-probleem op te lossen wanneer stalen van producten die uit voorraad kunnen worden geconfigureerd, worden weergegeven als beschikbaar.
exl-id: 28b3f378-a790-4af6-9627-5bd8571523fd
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-47803: configureerbare productstalen die uit voorraad worden weergegeven zoals beschikbaar

De ACSD-47803-patch verhelpt het probleem waarbij configureerbare productstalen die niet in voorraad zijn, worden weergegeven als beschikbaar. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-47803. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

configureerbare productstalen die buiten de voorraad beschikbaar zijn, worden weergegeven.

<u> Stappen om </u> te reproduceren:

>[!NOTE]
>
>In de onderstaande stappen worden voorbeeldgegevens als voorbeeld gegeven.

1. In [!UICONTROL Commerce] Admin, ga **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** en plaats **[!UICONTROL Display Out of Stock Products]** aan *ja*.
1. Navigeer vanuit Beheer opnieuw naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en bewerk een configureerbaar product op de productbewerkingspagina (bijvoorbeeld WB04-SKU als u voorbeeldgegevens gebruikt):
   * Voor één van de configuratievarianten, plaats de hoeveelheid aan *0* (bijvoorbeeld, voor &quot;WB04-m-Paars&quot;).
1. Open nu het configureerbare product op de winkel.
1. Selecteer de productgrootte voor de configureerbare variant met nul voorraad (dat is &quot;M&quot;).

<u> Verwachte resultaten </u>:

De opties voor de items buiten de voorraad worden uitgeschakeld en gemarkeerd als [!UICONTROL Out of Stock] .

<u> Ware resultaten </u>:

Alle kleurstalen zijn ingeschakeld, ook het staal dat [!UICONTROL Out of Stock] is.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
