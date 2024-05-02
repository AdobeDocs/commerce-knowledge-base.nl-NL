---
title: '"ACSD-51149: gepland [!UICONTROL ImportExport] met ingeschakeld [!UICONTROL Catalog Permissions] invalidates indexers'''
description: Pas de ACSD-51149-patch toe om het probleem met de Adobe Commerce-prestaties op te lossen op de plaats waar de patch is gepland [!UICONTROL ImportExport] met ingeschakeld [!UICONTROL Catalog Permissions] Maakt indexen ongeldig.
feature: Cache, Data Import/Export
role: Admin
exl-id: 3a26f4be-8e52-407d-bb25-2841458f3aa5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51149: gepland [!UICONTROL ImportExport] met ingeschakeld [!UICONTROL Catalog Permissions] validates indexers

De ACSD-51149-patch verhelpt het probleem waarbij de geplande oplossing [!UICONTROL ImportExport] met ingeschakeld [!UICONTROL Catalog Permissions] Maakt indexen ongeldig. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-51149. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gepland [!UICONTROL ImportExport] met ingeschakeld [!UICONTROL Catalog Permissions] Maakt indexen ongeldig.

<u>Stappen om te reproduceren</u>:

1. Inschakelen *[!UICONTROL Catalog Permissions]*.
1. Alle indexen instellen op *[!UICONTROL Update by Schedule]*.
1. Maak een eenvoudig product.
1. Dit product exporteren via **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. De geëxporteerde CSV downloaden en in `<AC root folder>/var/import`.
1. Maak een geplande productimport met de gedownloade CSV.
1. Voer de volledige redex uit.
1. Controleer de status van de indexeerders. Alle indexeerders moeten in *[!UICONTROL Ready]* status.
1. Voer de gemaakte geplande import uit vanuit het raster.
1. Controleer de status van de indexen opnieuw.

<u>Verwachte resultaten</u>:

Alle indexen bevinden zich in de *[!UICONTROL Ready]* status.

<u>Werkelijke resultaten</u>:

Sommige indexen bevinden zich in *[!UICONTROL Reindex Required]* status.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
