---
title: "ACSD-47106: nieuw aangepast kenmerk op pagina voor het maken van bedrijven niet opgeslagen"
description: Pas de ACSD-47106-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een waarde niet kan worden opgeslagen in een nieuw aangepast kenmerk op een pagina voor het maken van bedrijven.
exl-id: 941d6d8f-36eb-4b50-980f-e4afe6bf33df
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-47106: nieuw aangepast kenmerk op pagina voor het maken van bedrijven niet opgeslagen

De ACSD-47106-patch verhelpt het probleem dat een waarde niet kan worden opgeslagen in een nieuw aangepast kenmerk op een pagina voor het maken van bedrijven. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 is geïnstalleerd. De patch-id is ACSD-47106. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een waarde kan niet worden opgeslagen in een nieuw aangepast kenmerk op een pagina voor het maken van een bedrijf.

<u>Vereisten</u>:

* B2B-modules worden geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Ga naar Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**.
1. Nieuw kenmerk maken: _Test 01_.
1. Ga naar Commerce Admin > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** > en maak een nieuw bedrijf met alle vereiste details.
1. Probeer een waarde toe te voegen aan het aangepaste kenmerk _Test 01_.
1. De waarde van het aangepaste kenmerk bijwerken _Test 01_.

<u>Verwachte resultaten</u>:

Wijzigingen worden opgeslagen.

<u>Werkelijke resultaten</u>:

Wijzigingen worden niet opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
