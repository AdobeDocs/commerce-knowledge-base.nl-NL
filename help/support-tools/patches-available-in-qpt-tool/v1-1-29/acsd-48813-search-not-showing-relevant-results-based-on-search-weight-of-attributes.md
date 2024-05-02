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

De ACSD-48813-patch verhelpt het probleem waarbij de zoekopdracht geen relevante resultaten oplevert op basis van het zoekgewicht van de kenmerken. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-48813. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De zoekopdracht geeft geen relevante resultaten weer op basis van het zoekgewicht van de kenmerken.

<u>Stappen om te reproduceren</u>:

1. Installeer Adobe Commerce met voorbeeldgegevens.
1. De zoekengine instellen als [!DNL Elasticsearch].
1. Meld u aan als beheerder.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**.
1. Open de *name* kenmerk.
1. Open de winkel *[!UICONTROL Properties]* tab.
1. Selecteren [!UICONTROL Search Weight] = *10* in de vervolgkeuzelijst.
1. Klik op **[!UICONTROL Save Attribute]**.
1. Open nu de winkel en zoek naar het woord *Vorige*.

<u>Verwachte resultaten</u>:

Backpack-producten worden boven aan zoekresultaten geretourneerd.

<u>Werkelijke resultaten</u>:

Backpack-producten worden halverwege de zoekresultaten geretourneerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
