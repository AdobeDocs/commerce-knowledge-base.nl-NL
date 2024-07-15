---
title: 'MDVA-30972: bestelling status onjuiste verzending gemaakt via REST API'
description: Met de MDVA-30972-patch wordt het probleem opgelost waarbij de status van de bestelling onjuist wordt gewijzigd tijdens het maken van de zending via REST API. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd.
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972: bestelling status onjuiste verzending gemaakt via REST API

Met de MDVA-30972-patch wordt het probleem opgelost waarbij de status van de bestelling onjuist wordt gewijzigd tijdens het maken van de zending via REST API. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 geïnstalleerd is.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 tot 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een gedeeltelijke verzending van Admin via REST API voor een orde met *Vermoedelijke de ordestatus van het Fraude* wordt gecreeerd, wordt de ordestatus veranderd in *Verwerking*. Het zou bij *Vermoedelijke Fraude* moeten blijven.

<u> Eerste vereisten </u>:

* PayPal EC of een andere online betalingsmethode is ingesteld.
* Integratie voor REST API is ingesteld.

<u> Stappen om </u> te reproduceren:

1. Maak een bestelling met twee of meer items.
1. Login aan **Admin** > **Verkoop** > **Orders**. Open de volgorde die u zojuist hebt gemaakt.
1. Voor de pagina van de ordedetails, scrol neer aan **het Totaal van de Orde**. Klik op de **drop-down Status** en selecteer *Verdacht fraude*. Dan klik **voorleggen Commentaar** knoop.
1. Controle dat de orde *Verdacht Fraude* status nu heeft.
1. Een verzending maken voor één item van de bestelling met REST API:

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. Open de bestelling opnieuw in Beheer en controleer de status ervan.

<u> Verwachte resultaten </u>:

* De Status van de orde = *Vermoedelijke fraude*.
* De status van de bestelling wordt niet gewijzigd als dezelfde verzending wordt gemaakt via Admin.

<u> Ware resultaten </u>:

De Status van de orde = *verwerking*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
