---
title: '"ACSD-48313: [!UICONTROL configurable_variations] kolom niet geparseerd als kenmerkwaarde komma''s bevat'
description: Pas de ACSD-48313-patch toe om het Adobe Commerce-probleem op te lossen waarbij de [!UICONTROL configurable_variations] de kolom wordt niet geparseerd als de kenmerkwaarde een komma bevat.
exl-id: 0ac3f8da-4da3-4308-bea4-98a5b6926b0d
feature: Attributes, Configuration
role: Admin
source-git-commit: 4cb43c4f16238253fc7fc75d9af9b921dfa74158
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-48313: **[!UICONTROL configurable_variations]** kolom niet geparseerd als kenmerkwaarde komma bevat

De ACSD-48313-patch lost het probleem op waarbij **[!UICONTROL configurable_variations]** de kolom wordt niet geparseerd als de kenmerkwaarde een komma bevat. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 is geïnstalleerd. De patch-id is ACSD-48313. De versie waarin dit probleem wordt opgelost, is nog niet beschikbaar.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Na het exporteren van configureerbare producten kan het resulterende bestand niet opnieuw worden geïmporteerd vanwege een opmaakprobleem met de **[!UICONTROL configurable_variations]** kenmerk. Dit gebeurt wanneer er kenmerkopties zijn die een komma bevatten.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** en maak een nieuw kenmerk _Grootte_:
1. Invoertype catalogus voor winkeleigenaar: **[!UICONTROL Dropdown]**.
1. Opties maken die een komma bevatten, bijvoorbeeld:
   * 10,2 cm
   * 15,5 cm
1. **[!UICONTROL Advanced Attribute Properties]** - Toepassingsgebied: _Algemeen_.
1. Maak een nieuw configureerbaar product met de functie Configuraties maken.
1. Selecteer het bovenstaande kenmerk _Grootte_ en de twee opties die de komma bevatten.
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** en maak een nieuwe export van Producten (voer de uitsnede uit om het genereren van het CSV-bestand te activeren).
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** en probeer hetzelfde CSV-bestand dat u hierboven hebt gemaakt opnieuw te importeren.

<u>Verwachte resultaten</u>:

De gebruiker moet het bestand kunnen importeren.

<u>Werkelijke resultaten</u>:

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
