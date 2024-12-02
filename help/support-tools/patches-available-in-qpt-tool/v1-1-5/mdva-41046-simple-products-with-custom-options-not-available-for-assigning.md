---
title: 'MDVA-41046: eenvoudige producten met aangepaste opties die niet beschikbaar zijn voor toewijzing'
description: De patch MDVA-41046 lost het probleem op waar de eenvoudige producten met douaneopties niet beschikbaar voor het toewijzen aan configureerbaar/gegroepeerd product zijn. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41046. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 01229a69-c72a-4189-9be5-1761073b74ee
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-41046: eenvoudige producten met aangepaste opties die niet beschikbaar zijn voor toewijzing

De patch MDVA-41046 lost het probleem op waar de eenvoudige producten met douaneopties niet beschikbaar voor het toewijzen aan configureerbaar/gegroepeerd product zijn. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 geïnstalleerd is. De patch-id is MDVA-41046. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Eenvoudige producten met aangepaste opties zijn niet beschikbaar voor toewijzing aan configureerbaar/gegroepeerd product.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product met aanpasbare opties en stel een waarde in voor het configureerbare kenmerk.
   * Het gebruik *Kleur* als configureerbare attributen, en selecteert *Geel* als kleurenwaarde.
1. Sla het eenvoudige product op.
1. Ga nu naar de aanpasbare productpagina maken.
1. Ga door de &quot;creeer configuratie&quot;tovenaar en zorg ervoor om *Geel* als attributenkleur te selecteren.
1. Als u het configureerbare product niet wilt opslaan, selecteert u de optie &quot;Kies een ander product&quot; in het vervolgkeuzemenu Selecteren.
1. Hiermee wordt een productraster geopend dat met geel kleurkenmerk is gefilterd. Selecteer nu het eenvoudige product dat eerder met aanpasbare opties werd gecreeerd.
1. Sla het configureerbare product op.

<u> Verwachte resultaten </u>:

Het eenvoudige product met aangepaste opties is beschikbaar voor toewijzing (zichtbaar in het raster) in stap 6.

<u> Ware resultaten </u>:

De sectie Configuratie is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
