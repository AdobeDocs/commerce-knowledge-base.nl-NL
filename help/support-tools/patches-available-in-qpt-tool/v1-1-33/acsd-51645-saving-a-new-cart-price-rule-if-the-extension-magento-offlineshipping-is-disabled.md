---
title: 'ACSD-51645: Een nieuwe regel voor winkelwagentprijzen opslaan als de extensie Magento_OfflineShipping is uitgeschakeld'
description: Pas de ACSD-51645-patch toe om het Adobe Commerce-probleem op te lossen waarbij een fout optreedt bij het opslaan van een nieuwe regel voor winkelprijzen als de extensie Magento_OfflineShipping is uitgeschakeld.
exl-id: 301086bb-7aab-4e74-93e6-9080eebcb026
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-51645: Een nieuwe regel voor winkelwagentprijzen opslaan als de extensie Magento_OfflineShipping is uitgeschakeld

De ACSD-51645-patch verhelpt het probleem waarbij een fout optreedt bij het opslaan van een nieuwe prijsregel voor winkelwagentjes als de extensie Magento_OfflineShipping is uitgeschakeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-51645. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Fout bij het opslaan van een nieuwe regel voor winkelprijzen als de extensie `Magento_OfflineShipping` is uitgeschakeld.

<u>Stappen om te reproduceren</u>:

1. Schakel het dialoogvenster `Magento_OfflineShipping` -module.
1. Aanmelden bij **Beheerder**.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**.
1. Een nieuwe **[!UICONTROL Cart Price Rule]**.
1. Vul de vereiste velden.
1. Sla de **[!UICONTROL Cart Price Rule]**.

<u>Verwachte resultaten</u>:

De regel voor winkelprijzen is opgeslagen.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op:
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
