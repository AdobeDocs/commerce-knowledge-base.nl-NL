---
title: 'MDVA-38728: Als u de zichtbaarheid van een product wijzigt, wordt de URL voor het wijzigen van de hoofdwebsite gewijzigd.'
description: Met de MDVA-38728-patch wordt het probleem opgelost waarbij door het wijzigen van de productzichtbaarheid van de tweede website een URL voor herschrijven van de hoofdwebsite wordt gemaakt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-38728. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: ad1d5f82-294d-485d-acd3-28c3cd0fbf56
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-38728: Als u de zichtbaarheid van een product wijzigt, wordt de URL voor het wijzigen van de hoofdwebsite gewijzigd.

Met de MDVA-38728-patch wordt het probleem opgelost waarbij door het wijzigen van de productzichtbaarheid van de tweede website een URL voor herschrijven van de hoofdwebsite wordt gemaakt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 geïnstalleerd is. De patch-id is MDVA-38728. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u de productzichtbaarheid van de tweede website wijzigt, wordt de URL voor het wijzigen van de hoofdwebsite gewijzigd.

<u> Stappen om </u> te reproduceren:

1. Maak een extra website, winkel en winkelvoorvertoning.
1. Maak een eenvoudig product.
1. Plaats het zicht aan **niet Zichtbaar individueel**.
1. Alleen product toewijzen aan de tweede website.
1. Vul alle andere vereiste velden in.
1. Sla het product op.
1. MySQL-wachtrijen starten:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. Ga naar de productlijst.
1. Selecteer het gemaakte product en werk het zichtbaarheidskenmerk bij met behulp van de massatoeage die u wilt bijwerken naar Catalog en Search.
1. Controleer of de URL is herschreven.

<u> Verwachte resultaten </u>:

Het herschrijven wordt gemaakt voor de tweede website waaraan het product is toegewezen.

<u> Ware resultaten </u>:

Het herschrijven wordt gemaakt voor de hoofdwebsite.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
