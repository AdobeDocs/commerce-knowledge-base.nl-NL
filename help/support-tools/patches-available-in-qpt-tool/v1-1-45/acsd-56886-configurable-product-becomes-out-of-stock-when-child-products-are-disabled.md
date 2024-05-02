---
title: "ACSD-56886: configureerbaar product komt uit voorraad wanneer kinderproducten uitgeschakeld zijn"
description: Pas de ACSD-56886-patch toe om het Adobe Commerce-probleem op te lossen waarbij het configureerbare product uit voorraad komt te zitten wanneer de producten worden uitgeschakeld.
feature: Products
role: Admin, Developer
exl-id: 809b9829-283f-4e3c-bf27-1944057f944f
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56886: configureerbaar product is niet meer beschikbaar als onderliggende producten zijn uitgeschakeld

De ACSD-56886-patch verhelpt het probleem waarbij het configureerbare product uit voorraad raakt als onderliggende producten worden uitgeschakeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 is geïnstalleerd. De patch-id is ACSD-56886. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het configureerbare product wordt uit voorraad wanneer de kindproducten worden onbruikbaar gemaakt.

<u>Stappen om te reproduceren</u>:

1. Meld u aan als beheerder.
1. Alle indexen in het dialoogvenster instellen **[!UICONTROL Update By Schedule]** -modus.
1. Maak het volgende configureerbare product:

   * Naam = *CONFIGURATIETEST 1*
   * Kenmerk = *kleur*
   * Waarden = *rood* en *zwart*
   * Prijs van de **rood**  onderliggend product = *$ 100*;
   * Prijs van het &quot;zwarte&quot; onderliggende product = *$ 200*.

1. Maak de volgende geplande update voor het configureerbare product:

   * Begindatum = *3* minuten later.
   * Einddatum = *5* minuten na begindatum.
   * Productnaam = *CONFIGURABLE 1 TESTEN BEWERKT*.
   * Schakel het dialoogvenster **rood** kinderproduct in **Configureerbaar** sectie.

1. Wacht op de Begindatum.
1. Open de configureerbare productdetails op de Storefront.

<u>Verwachte resultaten</u>:

Het configureerbare product wordt weergegeven als **In voorraad** met de **Slechts 200** label.

<u>Werkelijke resultaten</u>:

Het configureerbare product wordt weergegeven als **Onvoldoende voorraad**.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
