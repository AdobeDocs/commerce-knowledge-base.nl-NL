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

De MDVA-35982-patch verhelpt de fout wanneer een beheerder die beperkt is tot een specifieke website, geen verzending kan maken voor de bestelling die op dezelfde website is geplaatst. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 geïnstalleerd is. De patch-id is MDVA-35982. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Merchant kan bepaalde bestellingen niet verzenden.

<u> Stappen om </u> te reproduceren:

1. Kies een productwebsite voor het product, behalve de standaardwinkel. Zie [ Product in Websites ](https://docs.magento.com/user-guide/catalog/settings-basic-websites.html) in onze gebruikersgids voor gedetailleerde stappen.
1. Maak een gebruikersrol voor de beheerder met aangepaste rolmodellen waarin de standaardwebsite/winkel niet is geselecteerd. Zie [ een rol ](https://docs.magento.com/user-guide/system/permissions-user-roles.html#define-a-role) in onze gebruikersgids voor gedetailleerde stappen bepalen.
1. Open het product op geef wijze uit en plaats een Prijs van de Groep voor dit product, in **Geavanceerde Prijsbepaling**. Zie [ Prijs van de Groep ](https://docs.magento.com/user-guide/catalog/product-price-group.html) in onze gebruikersgids voor gedetailleerde stappen.
1. Maak een bestelling met dit product.
1. Meld u aan onder Beheer met deze gebruikersrol en maak een verzending. Zie [ Creërend een Verzending ](https://docs.magento.com/user-guide/sales/shipments-create.html) in onze gebruikersgids voor gedetailleerde stappen.

<u> Verwachte resultaten </u>:

De verzending wordt gemaakt.

<u> Ware resultaten </u>:

De volgende fout wordt weergegeven:

`"0":"Notice: Undefined offset: XX in \/vendor\/magento\/module-catalog\/Model\/Product\/Attribute\/Backend\/GroupPrice\/AbstractGroupPrice.php on line 290"`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
