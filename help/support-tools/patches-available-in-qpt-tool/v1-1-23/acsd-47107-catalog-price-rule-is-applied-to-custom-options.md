---
title: 'ACSD-47107: regel voor catalogusprijzen wordt toegepast op aangepaste opties'
description: Pas de ACSD-47107-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de regel voor catalogusprijzen wordt toegepast op aangepaste opties.
exl-id: 5de2a87e-90c1-4a2a-a75c-7f9ca766868e
feature: Catalog Management, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-47107: catalogusprijsregel wordt toegepast op aangepaste opties

De ACSD-47107-patch verhelpt het probleem waarbij de regel voor catalogusprijzen wordt toegepast op aangepaste opties. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 is geïnstalleerd. De patch-id is ACSD-47107. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De catalogusprijsregel wordt toegepast op aangepaste opties.

<u>Stappen om te reproduceren</u>:

1. Maak een regel voor catalogusprijzen.
1. Instellen op *Toepassen als een percentage van de oorspronkelijke prijs* en voeg een korting van 10% toe.
1. Selecteer een product.
1. Maak enkele aangepaste opties.
1. Controleer de prijs op de voorkant.

<u>Verwachte resultaten</u>:

Catalogusprijsregel wordt niet toegepast op aangepaste opties, maar alleen op de oorspronkelijke prijs van het product.

<u>Werkelijke resultaten</u>:

De catalogusprijsregel wordt toegepast op aangepaste opties.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
