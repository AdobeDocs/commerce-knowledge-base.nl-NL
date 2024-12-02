---
title: 'MDVA-44044: Product wordt niet op categoriepagina weergegeven nadat het aan een nieuwe website is toegewezen'
description: Met de MDVA-44044-patch wordt het probleem opgelost waarbij een product niet op de categoriepagina wordt weergegeven nadat het aan een nieuwe website is toegewezen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 is geïnstalleerd. De patch-id is MDVA-44044. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: e3a179ed-243c-4200-a01a-796657bd31ab
feature: Categories, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-44044: Product wordt niet op categoriepagina weergegeven nadat het aan een nieuwe website is toegewezen

Met de MDVA-44044-patch wordt het probleem opgelost waarbij een product niet op de categoriepagina wordt weergegeven nadat het aan een nieuwe website is toegewezen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 geïnstalleerd is. De patch-id is MDVA-44044. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het product wordt niet op de categoriepagina weergegeven nadat het aan een nieuwe website is toegewezen.

<u> Stappen om </u> te reproduceren:

1. Stel de indexeermodus in op plannen.
1. Maak een secundaire website, sla deze op en sla de weergave op.
1. Voeg een secundaire archiefcode toe in `index.php`:

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. Maak een nieuwe categorie.
1. Maak een nieuw product dat is toegewezen aan de nieuwe categorie. Let erop dat u het alleen toewijst aan de primaire website.
1. Voer de uitsnede uit.
1. Open de categorie vanuit de winkel.
1. Wijs het product toe aan de secundaire website.
1. Voer de uitsnede opnieuw uit.

<u> Verwachte resultaten </u>:

Het product wordt op de categoriepagina weergegeven na een geplande indexeerprogramma.

<u> Ware resultaten </u>:

Het product wordt pas op de categoriepagina weergegeven als het volledig opnieuw is samengesteld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
