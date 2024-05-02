---
title: 'ACSD-54007: Ongedefinieerde fout _scope met arraysleutel bij het importeren van klantgegevens'
description: Pas de ACSD-54007-patch toe om het Adobe Commerce-probleem op te lossen waarbij een Undefined array key_scope-fout wordt weergegeven bij het importeren van klantgegevens.
feature: Data Import/Export
role: Admin, Developer
exl-id: b14a14fd-5021-460f-8ca9-c9845859df97
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-54007: Ongedefinieerde fout _scope met arraysleutel bij het importeren van klantgegevens

De ACSD-54007-patch verhelpt het probleem waarbij een *Ongedefinieerde array key_scope* fout bij het importeren van klantgegevens. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 is geïnstalleerd. De patch-id is ACSD-54007. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bij het importeren van klantgegevens ziet u een *Ongedefinieerde array key_scope* fout.

<u>Stappen om te reproduceren</u>:

1. Ga naar Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** >  **[!UICONTROL Import]**, set **[!UICONTROL Entity Type]** tot **[!UICONTROL Stock Sources]** en importeer het CSV-bestand van de voorraadbron (dat broncode, SKU, hoeveelheid en status bevat).
1. Kies Klanten en adressen (één bestand) en importeer het CSV-bestand, dat de adresgegevens van de klant bevat.

<u>Verwachte resultaten</u>:

Er treden geen fouten op.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op:  *Waarschuwing: niet-gedefinieerde arraysleutel &quot;_scope&quot; in /var/www/html/vendor/magento/module-customer-import-export/Model/ResourceModel/Import/CustomerComposite/Data.php op regel 84*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
