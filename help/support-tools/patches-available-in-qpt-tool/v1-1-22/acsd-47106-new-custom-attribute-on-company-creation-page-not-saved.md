---
title: 'ACSD-47106: nieuw aangepast kenmerk op pagina voor het maken van bedrijven niet opgeslagen'
description: Pas de ACSD-47106-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een waarde niet kan worden opgeslagen in een nieuw aangepast kenmerk op een pagina voor het maken van bedrijven.
exl-id: 941d6d8f-36eb-4b50-980f-e4afe6bf33df
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-47106: nieuw aangepast kenmerk op pagina voor het maken van bedrijven niet opgeslagen

De ACSD-47106-patch verhelpt het probleem dat een waarde niet kan worden opgeslagen in een nieuw aangepast kenmerk op een pagina voor het maken van bedrijven. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 wordt geïnstalleerd. De patch-id is ACSD-47106. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een waarde kan niet worden opgeslagen in een nieuw aangepast kenmerk op een pagina voor het maken van een bedrijf.

<u> Eerste vereisten </u>:

* B2B-modules worden geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Ga naar Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]** .
1. Creeer nieuwe attributen: _Test 01_.
1. Ga naar Commerce Admin > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** > en maak een nieuw bedrijf met alle vereiste details.
1. Probeer om een waarde aan de douane toe te voegen kenmerkt _Test 01_.
1. Probeer om de waarde van de douane attributen _Test 01_ bij te werken.

<u> Verwachte resultaten </u>:

Wijzigingen worden opgeslagen.

<u> Ware resultaten </u>:

Wijzigingen worden niet opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
