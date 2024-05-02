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

De ACSD-47803-patch verhelpt het probleem waarbij configureerbare productstalen die niet in voorraad zijn, worden weergegeven als beschikbaar. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-47803. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

configureerbare productstalen die buiten de voorraad beschikbaar zijn, worden weergegeven.

<u>Stappen om te reproduceren</u>:

>[!NOTE]
>
>In de onderstaande stappen worden voorbeeldgegevens als voorbeeld gegeven.

1. In de [!UICONTROL Commerce] Beheerder, ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** en stelt de **[!UICONTROL Display Out of Stock Products]** tot *Ja*.
1. Navigeer opnieuw vanuit Beheer naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en bewerk een configureerbaar product in de productbewerkingspagina (bijvoorbeeld &quot;WB04&quot; SKU, als u steekproefgegevens gebruikt):
   * Voor een van de configuratievarianten stelt u de hoeveelheid in op *0* (bijvoorbeeld voor &quot;WB04-M-Purple&quot;).
1. Open nu het configureerbare product op de winkel.
1. Selecteer de productgrootte voor de configureerbare variant met nul voorraad (dat is &quot;M&quot;).

<u>Verwachte resultaten</u>:

De opties voor het buiten-de-voorraadsysteem zijn uitgeschakeld en gemarkeerd als [!UICONTROL Out of Stock].

<u>Werkelijke resultaten</u>:

Alle kleurstalen zijn ingeschakeld, ook het kleurstaal dat [!UICONTROL Out of Stock].

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
