---
title: 'MDVA-39181: producten uit categorie "niet gedefinieerd" in regel worden in de desbetreffende productregels vermeld'
description: Met de MDVA-39181-patch wordt het probleem opgelost waarbij gerelateerde productregels producten uit een categorie weergeven die niet in de regel is gedefinieerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-39181. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181: producten uit categorie &quot;niet gedefinieerd&quot; in regel worden in de desbetreffende productregels vermeld

Met de MDVA-39181-patch wordt het probleem opgelost waarbij gerelateerde productregels producten uit een categorie weergeven die niet in de regel is gedefinieerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 geïnstalleerd is. De patch-id is MDVA-39181. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De verwante productregels tonen producten uit categorieën die niet in de regel worden bepaald.

<u> Eerste vereisten </u>:

Voorbeeldgegevens installeren.

<u> Stappen om </u> te reproduceren:

1. Creeer een attributenmerk en voeg het aan de **Reeks van het Attribuut van Tops** toe.
1. Kies **toetreden**, **Augusta**, en **Ingrid** jassen om aan het Merk Kitty van **Vrouwen** toe te voegen > **Tops** > **categorie van Jasjes**.
1. Kies **Beaumont**, **Hyperion**, en **Kenobi** jassen om aan het Merk Kitty van **Mannen** toe te voegen > **Tops** > **categorie van het Jasje**.
1. Een verwant product maken met:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Producten afstemmen:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Te tonen producten:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Open SKU WJ04 van het vooreind en controleer verwante producten.
1. Werk categoriidentiteitskaart van **Vrouwen** > **Tops** > **Jasjes** bij voor het geval dat het van dit verschillend is.

<u> Verwachte resultaten </u>:

Alleen producten van hetzelfde merk en dezelfde kindercategorie worden in verwante producten vermeld.

<u> Ware resultaten </u>:

Verwante producten worden van hetzelfde merk getoond, maar van een willekeurige oudercategorie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
