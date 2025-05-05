---
title: 'MDVA-44533: Korting wordt onjuist toegepast op gebundeld onderliggend product'
description: De patch MDVA-44533 verhelpt het probleem waarbij een korting onjuist wordt toegepast op een gebundeld onderliggend product. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-44533. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 84302ed4-d850-45e4-8b5b-44495f9df820
feature: Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-44533: Korting wordt onjuist toegepast op gebundeld onderliggend product

De patch MDVA-44533 verhelpt het probleem waarbij een korting onjuist wordt toegepast op een gebundeld onderliggend product. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 geïnstalleerd is. De patch-id is MDVA-44533. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Korting wordt onjuist toegepast op een gebundeld onderliggend product.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product met een prijs van 50$.
1. Maak een gebundeld product en wijs het eenvoudige product als enige optie voor het gebundelde product toe.
1. Een prijsregel voor winkelwagentjes maken met:

   * Voorwaarde: als de totale hoeveelheid groter is dan 130$
   * Actie: korting voor vaste bedragen van 10$ wordt toegepast

1. Ga naar de winkel en voeg het bundelproduct aan de kar met hoeveelheid = 1 toe.
1. Ga naar het winkelwagentje en controleer of de totale kosten van het bundelproduct 50$ bedragen en of de korting niet van toepassing is.
1. Wijzig de hoeveelheid in 2 en werk de winkelwagen bij. De totale kosten van het gebundelde product moeten nu 100$ bedragen.

<u> Verwachte resultaten </u>:

De korting wordt niet toegepast omdat het subtotaal 100\$ is, wat minder dan 130\$ in de regelvoorwaarde is.

<u> Ware resultaten </u>:

De korting wordt toegepast.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
