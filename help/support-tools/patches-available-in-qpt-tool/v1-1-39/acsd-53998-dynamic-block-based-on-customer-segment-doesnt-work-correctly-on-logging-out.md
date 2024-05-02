---
title: 'ACSD-53998: Dynamisch blok op basis van klantensegment werkt onjuist na afmelden.'
description: Pas de ACSD-53998-patch toe om het Adobe Commerce-probleem op te lossen waarbij een dynamisch blok op basis van een klantsegment niet correct werkt nadat u zich hebt afgemeld bij een klantenaccount.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
exl-id: 5a82a6b8-e8f7-47ff-89f6-93a39b72fe38
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-53998: Dynamisch blok op basis van klantensegment werkt verkeerd na het afmelden

De ACSD-53998-patch verhelpt het probleem waarbij een dynamisch blok op basis van een klantensegment niet correct werkt nadat u zich hebt afgemeld bij een klantenaccount. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.39 is geïnstalleerd. De patch-id is ACSD-53998. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een dynamisch blok dat op een klantensegment wordt gebaseerd werkt niet correct na het programma openen van een klantenrekening.

<u>Vereisten</u>:

Installeren en inschakelen [!DNL Page Builder] modules.

<u>Stappen om te reproduceren</u>:

1. Maak twee klantsegmenten zonder voorwaarden.
1. Maak twee dynamische blokken voor elk segment.
1. Een blok maken met de twee dynamische blokken als [!DNL Page Builder] dynamische blokken.
1. Maak een widget met het bovenstaande blok en maak het blok zichtbaar onder de voettekstsectie van alle pagina&#39;s.
1. Wis de cache.
1. Open de startpagina.
1. Meld u aan als klant.
1. Afmelden.

<u>Verwachte resultaten</u>:

De banner die voor het programma geopende klanten wordt gecreeerd wordt niet getoond voor gastgebruikers.

<u>Werkelijke resultaten</u>:

De banner die voor het het programma geopende klantensegment wordt gecreeerd wordt getoond zelfs na het programma openen van de klantenrekening.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
