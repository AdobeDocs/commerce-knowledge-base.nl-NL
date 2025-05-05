---
title: 'MDVA-37592: Sorteren op prijs die niet werkt voor producten met prijs nul'
description: De MDVA-37592 Adobe Commerce-patch lost het probleem op dat sorteren op prijs niet correct werkt voor producten met prijs nul die aan een gedeelde catalogus worden toegewezen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 is geïnstalleerd. De patch-id is MDVA-37592. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592: Sorteren op prijs die niet werkt voor producten met prijs nul

De MDVA-37592 Adobe Commerce-patch lost het probleem op dat sorteren op prijs niet correct werkt voor producten met prijs nul die aan een gedeelde catalogus worden toegewezen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 geïnstalleerd is. De patch-id is MDVA-37592. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce op onze cloudarchitectuur 2.4.0-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatietypen) 2.3.6-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Sorteren op prijs werkt niet correct voor producten met prijs nul die aan een gedeelde catalogus wordt toegewezen.

<u> Eerste vereisten </u>:

B2B is geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Gedeelde catalogus inschakelen.
1. Maak vier producten met de volgende prijzen en wijs deze toe aan een categorie: $50, $60, $70 en $80.
1. Maak een gedeelde catalogus met de bovenstaande producten.
1. Stel de aangepaste prijs in op nul voor het product met een prijs van $70.
1. Creëer nu een bedrijfgebruiker en wijs het aan de gedeelde gemaakte catalogus toe.
1. Meld u aan met het bedrijfsaccount en blader naar de categorie waaraan de producten zijn toegewezen.
1. Probeer te sorteren op prijs.

<u> Verwachte resultaten </u>:

Het product met prijs nul wordt correct gesorteerd.

<u> Ware resultaten </u>:

Het product met prijs nul wordt NIET correct gesorteerd. In plaats daarvan wordt het gesorteerd op basis van de oorspronkelijke prijs.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelaarsdocumentatie toe.
* Adobe Commerce op onze wolkenarchitectuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
