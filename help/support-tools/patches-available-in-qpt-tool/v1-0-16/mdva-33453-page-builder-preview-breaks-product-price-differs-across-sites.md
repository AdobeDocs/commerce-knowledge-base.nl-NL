---
title: 'MDVA-33453: De voorvertoning van de Page Builder verbreekt de productprijs per site.'
description: Met de MDVA-33453-patch wordt het probleem opgelost waarbij de voorvertoning van de Page Builder wordt verbroken als overeenkomende producten een andere prijs hebben voor elke website. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: 78a7f7d4-8691-4b5d-a900-1c9a6ec73486
feature: CMS, Orders, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-33453: De voorvertoning van de Page Builder verbreekt de productprijs per site.

Met de MDVA-33453-patch wordt het probleem opgelost waarbij de voorvertoning van de Page Builder wordt verbroken als overeenkomende producten een andere prijs hebben voor elke website. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.4.1

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur en Adobe Commerce op-gebouw 2.3.6 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De voorvertoning van het product Page Builder wordt onderbroken wanneer er een product met verschillende prijzen op verschillende websites aanwezig is.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij het deelvenster Commerce Admin.
1. Maak twee websites.
1. Maak een eenvoudig product.
1. Stel een andere prijs in voor het product op elke website.
1. Uitsnijden en opnieuw indexeren.
1. Maak of bewerk een CMS-pagina en gebruik het productblok om het product toe te voegen.

<u> Ware resultaat </u>:<br>

De onderstaande fout treedt op:

*het filtreren van de Fout malplaatje: Punt (Magento\\Catalog\\Model\\Product\\Interceptor) met zelfde identiteitskaart &quot;2&quot;bestaat reeds.*

<u> Verwacht resultaat </u>:<br>

Er worden geen fouten weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
