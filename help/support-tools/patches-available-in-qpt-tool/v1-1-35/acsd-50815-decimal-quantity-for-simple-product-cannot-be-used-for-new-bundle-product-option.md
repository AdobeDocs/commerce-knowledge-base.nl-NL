---
title: "ACSD-50815: decimale hoeveelheid voor eenvoudig product kan niet worden gebruikt voor nieuwe gebundelde productoptie"
description: Pas de ACSD-50815-patch toe om het Adobe Commerce-probleem op te lossen waarbij de decimale hoeveelheid voor een eenvoudig product niet kan worden gebruikt voor een nieuwe gebundelde productoptie.
feature: Products
role: Admin
exl-id: f4aa417c-b0eb-4a68-bf1e-fd86770cc72d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-50815: decimale hoeveelheid voor eenvoudig product kan niet worden gebruikt voor nieuwe gebundelde productoptie

De ACSD-50815-patch verhelpt de kwestie waarbij de decimale hoeveelheid voor een eenvoudig product niet kan worden gebruikt voor een nieuwe gebundelde productoptie. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 is geïnstalleerd. De patch-id is ACSD-50815. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De decimale hoeveelheid voor een eenvoudig product kan niet worden gebruikt voor een nieuwe gebundelde productoptie.

<u>Stappen om te reproduceren</u>:

1. Meld u aan als beheerder.
1. Maak een nieuw eenvoudig product.
   * In de **[!UICONTROL Advanced Inventory]** venster, instellen [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes].
   * Sla het eenvoudige product op.
1. Maak een nieuw gebundeld product.
1. Voeg een willekeurige optie toe.
1. Voeg het eenvoudige product in deze optie toe.
1. Geef een decimale hoeveelheid voor het eenvoudige product op in de optie voor het gebundelde product. Bijvoorbeeld 1.5.

<u>Verwachte resultaten</u>:

Het is mogelijk decimale aantallen in te stellen. Er worden geen fouten weergegeven.

<u>Werkelijke resultaten</u>:

De fout, *Voer een geldig getal in dit veld in* wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
