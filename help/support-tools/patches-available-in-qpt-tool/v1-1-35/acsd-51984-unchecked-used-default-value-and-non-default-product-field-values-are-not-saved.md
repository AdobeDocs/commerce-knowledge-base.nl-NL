---
title: 'ACSD-51984: Niet-ingeschakeld [!UICONTROL Use Default Value] en niet-standaard productveldwaarden worden niet opgeslagen voor de tweede website, winkel en winkelweergave'
description: Pas de ACSD-51984-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de niet-geselecteerde [!UICONTROL Use Default Value] en niet-standaard productveldwaarden niet worden opgeslagen voor de tweede website-, opslag- en winkelweergave.
feature: Products
role: Admin
exl-id: 1f45c700-dd27-4a69-8634-9c0aa131d197
source-git-commit: f42fcacbe3b7174b2a3571afe80f5eedb8e9aa75
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-51984: Niet ingeschakeld *[!UICONTROL Use Default Value]* en niet-standaard productveldwaarden worden niet opgeslagen

>[!NOTE]
>
>Dit flard is verouderd en is vervangen door [ ACSD-54776 ](/help/support-tools/patches-available-in-qpt-tool/v1-1-39/acsd-54776-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) flard in de 1.1.39 versie QPT wordt toegevoegd.

De ACSD-51984-patch verhelpt het probleem dat de niet-geselecteerde **[!UICONTROL Use Default Value]** en niet-standaard productveldwaarden niet worden opgeslagen voor de tweede website, opslag en opslagweergave. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-51984. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Niet-geselecteerde *[!UICONTROL Use Default Value]* en niet-standaardwaarden voor productvelden worden niet opgeslagen voor de tweede website-, opslag- en winkelweergave.

<u> Stappen om </u> te reproduceren:

1. Ga naar de achterkant en navigeer naar **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** en maak een nieuwe website, sla deze op en sla de weergave op.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** , maak een eenvoudig product en sla het op en wijs het product via **[!UICONTROL Product in Websites]** toe aan beide websites.
1. Verander het werkingsgebied in de pas gecreëerde opslagmening van stap 2.
1. Ga naar **[!UICONTROL Search Engine Optimization]** en schakel de selectievakjes **[!UICONTROL Use Default Value]** voor [!UICONTROL Meta Title] , [!UICONTROL Meta Keywords] en [!UICONTROL Meta Description] uit.
1. Reinig de tekst in de velden *[!UICONTROL Meta Title]* , *[!UICONTROL Meta Keywords]* en *[!UICONTROL Meta Description]* en klik op **[!UICONTROL Save]** .
1. Ga nogmaals naar **[!UICONTROL Search Engine Optimization]** .

<u> Verwachte resultaten </u>

De waarden voor de velden en voor de selectievakjes worden opgeslagen.

<u> Ware resultaten </u>

De waarden voor de velden en voor de selectievakjes worden niet opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] gids.