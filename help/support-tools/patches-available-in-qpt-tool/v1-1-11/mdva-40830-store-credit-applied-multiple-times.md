---
title: 'MDVA-40830: Winkelkrediet wordt meerdere keren toegepast tijdens bestelling'
description: De patch MDVA-40830 verhelpt het probleem waarbij het winkelkrediet meerdere keren wordt toegepast tijdens de plaatsing van de bestelling. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 is geïnstalleerd. De patch-id is MDVA-40830. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 218a100a-4500-4ef5-bbdb-fbbd12f2fa26
feature: Orders, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-40830: Winkelkrediet wordt meerdere keren toegepast tijdens bestelling

De patch MDVA-40830 verhelpt het probleem waarbij het winkelkrediet meerdere keren wordt toegepast tijdens de plaatsing van de bestelling. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 geïnstalleerd is. De patch-id is MDVA-40830. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.7-p2, 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het winkelkrediet wordt meerdere keren toegepast tijdens de plaatsing van de bestelling.

<u> Stappen om </u> te reproduceren:

1. Maak een klant en voeg winkelkrediet toe aan de klantenaccount.
1. Voeg een eenvoudig product toe aan de wagen.
1. Verzendadres en factuuradres voor de winkelwagen instellen.
1. Controleer het grote_totaal van de wagen.
1. Pas superieure creditering op de winkelwagentje toe met behulp van de volgende GraphQL-aanvraag:

<pre>
<code class="language-graphql">
mutation &lbrace;
  applyStoreCreditToCart(
    input: { cart_id: "%cartId%" }
  ) &lbrace;
    cart &lbrace;
      prices &lbrace;
        grand_total &lbrace;
          currency
          value
        &rbrace;
      &rbrace;
      applied_store_credit &lbrace;
        applied_balance &lbrace;
          currency
          value
        &rbrace;
        current_balance &lbrace;
          currency
          value
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u> Verwachte resultaten </u>:

De waarde van applied_store_credit wordt correct toegepast, en het karttotalen worden correct weerspiegeld in de API reactie.

<u> Ware resultaten </u>:

De waarde van applied_store_credit wordt tweemaal toegepast, die zowel het karretje als het ale_total beïnvloedt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
