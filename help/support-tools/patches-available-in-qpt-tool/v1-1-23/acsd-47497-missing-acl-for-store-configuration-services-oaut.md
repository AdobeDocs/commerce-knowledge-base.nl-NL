---
title: 'ACSD-47497: ontbrekende ACL voor Store/Configuration/Services [!UICONTROL OAuth]'
description: Pas de ACSD-47497-patch toe om het Adobe Commerce-probleem op te lossen wanneer machtigingen voor een bepaalde rol zijn ingesteld en u kunt geen toegang tot de configuratiesectie definiëren.
exl-id: c13fd541-1379-4893-9190-9da1422b2b99
feature: Configuration, Identity Management, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-47497: ontbrekende ACL voor Store/Configuration/Services [!UICONTROL OAuth]

De ACSD-47497-patch lost het probleem op waarbij de **[!UICONTROL Services]** is niet zichtbaar in het dialoogvenster **[!UICONTROL Configuration]** in Adobe Commerce Admin. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 is geïnstalleerd. De patch-id is ACSD-47497. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer de toestemmingen voor een bepaalde rol worden geplaatst, kunt u geen toegang tot bepalen **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de Adobe Commerce-beheerder. Ga naar **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. Selecteren **[!UICONTROL Role Resources]** in de rol Beheerders en ingesteld **[!UICONTROL Resource Access]** krachtens **[!UICONTROL Roles Resources]** tot _Aangepast_ Selecteer vervolgens alle selectievakjes. Selecteren **[!UICONTROL Save Role]**.
1. Selecteren **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]**. De **[!UICONTROL OAuth]** configuratiesectie is niet beschikbaar.

<u>Verwachte resultaten</u>:

In **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**, is de configuratiesectie zichtbaar.

<u>Werkelijke resultaten</u>:

In **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**, ontbreekt de sectie Configuratie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
