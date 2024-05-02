---
title: '"ACSD-48634: [!DNL JS] fouten bij [!DNL Google Analytics Content Experiments] enabled'''
description: Pas de ACSD-48634-patch toe om deze te repareren [!DNL JS] fouten op een [!DNL staging] pagina bijwerken wanneer [!DNL Google Analytics Content Experiments] is ingeschakeld.
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] fouten bij [!DNL Google Analytics Content Experiments] enabled

De ACSD-48634-patch corrigeert [!DNL JS] fouten op een [!DNL staging] pagina bijwerken wanneer [!DNL Google Analytics Content Experiments] is ingeschakeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-48634. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL JS] fouten optreden op een [!DNL staging] pagina bijwerken wanneer [!DNL Google Analytics Content Experiments] is ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. In **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, een extra website maken, opslaan en **[!UICONTROL Store View]**. Zorg ervoor dat de **[!UICONTROL Store View]** is *[!UICONTROL Enabled]*.
1. Configureren **[!DNL Configure Google Analytics]** door naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * Voor **[!DNL Main]** en aanvullende websites [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* voor andere velden, maar wijzig deze niet.
   * Voor **[!DNL Default Config]** [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Uitschakelen **[!DNL Configure Google Analytics]** op **[!DNL Default Config]** [!DNL scope] door wijzigen **[!UICONTROL Enable]** van *[!UICONTROL Yes]* tot *[!UICONTROL No]*. Verander niets anders!
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Maak en bewerk om het even welke **[!UICONTROL category]** en voeg er een geplande update voor toe:
   * Elke naam, begindatum in de toekomst, einddatum in de toekomst en elke wijziging in **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. De update opslaan en de [!DNL browser developer console] voor fouten.

<u>Verwachte resultaten</u>:

Nee [!DNL JS] fouten en de wijzigingen in de [!DNL staging] de update is opgeslagen.

<u>Werkelijke resultaten</u>:

[!DNL JS] fouten zijn zichtbaar in de console, het formulier is beschadigd en [!DNL spinner] wordt nooit uitgeschakeld na het opslaan.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
