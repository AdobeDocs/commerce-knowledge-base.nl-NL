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

De ACSD-51645-patch verhelpt het probleem waarbij een fout optreedt bij het opslaan van een nieuwe prijsregel voor winkelwagentjes als de extensie Magento_OfflineShipping is uitgeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-51645. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL>) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een fout opgehaald bij het opslaan van een nieuwe regel voor startprijs als de extensie `Magento_OfflineShipping` is uitgeschakeld.

<u> Stappen om </u> te reproduceren:

1. Schakel de module `Magento_OfflineShipping` uit.
1. Login aan **Admin**.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** .
1. Maak een nieuwe **[!UICONTROL Cart Price Rule]** .
1. Vul de vereiste velden.
1. Sla de **[!UICONTROL Cart Price Rule]** op.

<u> Verwachte resultaten </u>:

De regel voor winkelprijzen is opgeslagen.

<u> Ware resultaten </u>:

De volgende fout treedt op:
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL>) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL>) in de [!DNL Quality Patches Tool] gids.
