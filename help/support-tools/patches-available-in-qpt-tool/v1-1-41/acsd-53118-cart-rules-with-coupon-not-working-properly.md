---
title: 'ACSD-53118: Rijregels met coupon werken niet correct'
description: Pas de ACSD-53118-patch toe om de Adobe Commerce-uitgave te herstellen waar de regel van de winkelwagenprijs wordt toegepast met behulp van een couponcode, terwijl het product in het winkelwagentje een leeg matchingkenmerk heeft.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: a660ddb3-03fc-4460-b2a8-8e851f57e7a9
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-53118: Rijregels met coupon werken niet correct

De ACSD-53118-patch corrigeert de kwestie waar de regel van de winkelwagenprijs wordt toegepast met behulp van een couponcode terwijl het product in de winkelwagen een leeg matchingkenmerk heeft. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 wordt geïnstalleerd. De patch-id is ACSD-53118. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijsregel voor winkelwagentjes wordt toegepast met behulp van een couponcode terwijl het product in het winkelwagentje een leeg matchingskenmerk heeft.

<u> Stappen om </u> te reproduceren:

1. Maak een prijskenmerk en voeg dit toe aan de kenmerkset. Maak het attribuut bruikbaar in de voorwaarden van de bevorderingsregel.
1. Maak een product en laat het nieuwe kenmerk leeg.
1. Maak een regel voor de kartonprijs met een specifieke coupon en de volgende voorwaarde:

   * Als een item in de winkelwagentje is GEVONDEN met ALLE van deze voorwaarden true: Attribute1 is 0.

1. Voeg het product dat in Stap 2 wordt gecreeerd aan de kar toe.
1. Gebruik de couponcode voor de winkelregel die u in stap 3 hebt gemaakt.

<u> Verwachte resultaten </u>:

Er wordt geen korting toegepast op het winkelwagentje.

<u> Ware resultaten </u>:

Korting wordt toegepast op het winkelwagentje.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
