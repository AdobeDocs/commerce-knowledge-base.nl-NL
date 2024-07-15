---
title: 'ACSD-48813: zoekopdracht geeft geen relevante resultaten weer op basis van zoekgewicht van kenmerken'
description: Pas de ACSD-48813-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de zoekopdracht geen relevante resultaten oplevert op basis van het zoekgewicht van de kenmerken.
exl-id: 089e3ab3-0dfa-4f81-85c7-f6060f326d97
feature: Admin Workspace, Attributes, Search
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48813: zoekopdracht geeft geen relevante resultaten weer op basis van zoekgewicht van kenmerken

De ACSD-48813-patch verhelpt het probleem waarbij de zoekopdracht geen relevante resultaten oplevert op basis van het zoekgewicht van de kenmerken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-48813. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De zoekopdracht geeft geen relevante resultaten weer op basis van het zoekgewicht van de kenmerken.

<u> Stappen om </u> te reproduceren:

1. Installeer Adobe Commerce met voorbeeldgegevens.
1. Stel het zoekprogramma in op [!DNL Elasticsearch] .
1. Meld u aan als beheerder.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]** .
1. Open het *naam* attribuut.
1. Open de tab storefront *[!UICONTROL Properties]* .
1. Selecteer [!UICONTROL Search Weight] = *10* van de dropdown waarde.
1. Klik op **[!UICONTROL Save Attribute]**.
1. Nu open storefront en onderzoek naar het woord *terug*.

<u> Verwachte resultaten </u>:

Backpack-producten worden boven aan zoekresultaten geretourneerd.

<u> Ware resultaten </u>:

Backpack-producten worden halverwege de zoekresultaten geretourneerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
