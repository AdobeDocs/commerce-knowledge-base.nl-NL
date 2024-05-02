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

Met de MDVA-33453-patch wordt het probleem opgelost waarbij de voorvertoning van de Page Builder wordt verbroken als overeenkomende producten een andere prijs hebben voor elke website. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:** Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.6 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De voorvertoning van het product Page Builder wordt onderbroken wanneer er een product met verschillende prijzen op verschillende websites aanwezig is.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij het deelvenster Commerce Admin.
1. Maak twee websites.
1. Maak een eenvoudig product.
1. Stel een andere prijs in voor het product op elke website.
1. Uitsnijden en opnieuw indexeren.
1. Maak of bewerk een CMS-pagina en gebruik het productblok om het product toe te voegen.

<u>Werkelijk resultaat</u>:<br>

De onderstaande fout treedt op:

*Fout bij filteren van sjabloon: Item (Magento\\Catalog\\Model\\Product\\Interceptor) met dezelfde id &quot;2&quot; bestaat al.*

<u>Verwacht resultaat</u>:<br>

Er worden geen fouten weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
