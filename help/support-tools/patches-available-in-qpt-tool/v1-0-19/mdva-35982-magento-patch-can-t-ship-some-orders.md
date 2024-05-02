---
title: "MDVA-35982: Kan sommige bestellingen niet verzenden"
description: De MDVA-35982-patch verhelpt de fout wanneer een beheerder die beperkt is tot een specifieke website, geen verzending kan maken voor de bestelling die op dezelfde website is geplaatst. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35982. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: f41c6572-66bb-4697-93e3-da34b81829e2
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-35982: Kan sommige bestellingen niet verzenden

De MDVA-35982-patch verhelpt de fout wanneer een beheerder die beperkt is tot een specifieke website, geen verzending kan maken voor de bestelling die op dezelfde website is geplaatst. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35982. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Merchant kan bepaalde bestellingen niet verzenden.

<u>Stappen om te reproduceren</u>:

1. Kies een productwebsite voor het product, behalve de standaardwinkel. Zie [Product op websites](https://docs.magento.com/user-guide/catalog/settings-basic-websites.html) in onze gebruikershandleiding voor meer informatie.
1. Maak een gebruikersrol voor de beheerder met aangepaste rolmodellen waarin de standaardwebsite/winkel niet is geselecteerd. Zie [Een rol definiëren](https://docs.magento.com/user-guide/system/permissions-user-roles.html#define-a-role) in onze gebruikershandleiding voor meer informatie.
1. Open het product in bewerkingsmodus en stel een groepsprijs voor dit product in **Geavanceerde prijzen**. Zie [Groepsprijs](https://docs.magento.com/user-guide/catalog/product-price-group.html) in onze gebruikershandleiding voor meer informatie.
1. Maak een bestelling met dit product.
1. Meld u aan onder Beheer met deze gebruikersrol en maak een verzending. Zie [Een verzending maken](https://docs.magento.com/user-guide/sales/shipments-create.html) in onze gebruikershandleiding voor meer informatie.

<u>Verwachte resultaten</u>:

De verzending wordt gemaakt.

<u>Werkelijke resultaten</u>:

De volgende fout wordt weergegeven:

`"0":"Notice: Undefined offset: XX in \/vendor\/magento\/module-catalog\/Model\/Product\/Attribute\/Backend\/GroupPrice\/AbstractGroupPrice.php on line 290"`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
