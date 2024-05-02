---
title: "ACSD-53118: Rijregels met coupon werken niet correct"
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

De ACSD-53118-patch corrigeert de kwestie waar de regel van de winkelwagenprijs wordt toegepast met behulp van een couponcode terwijl het product in de winkelwagen een leeg matchingkenmerk heeft. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 is geïnstalleerd. De patch-id is ACSD-53118. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijsregel voor winkelwagentjes wordt toegepast met behulp van een couponcode terwijl het product in het winkelwagentje een leeg matchingskenmerk heeft.

<u>Stappen om te reproduceren</u>:

1. Maak een prijskenmerk en voeg dit toe aan de kenmerkset. Maak het attribuut bruikbaar in de voorwaarden van de bevorderingsregel.
1. Maak een product en laat het nieuwe kenmerk leeg.
1. Maak een regel voor de kartonprijs met een specifieke coupon en de volgende voorwaarde:

   * Als een item in de winkelwagentje is GEVONDEN met ALLE van deze voorwaarden true: Attribute1 is 0.

1. Voeg het product dat in Stap 2 wordt gecreeerd aan de kar toe.
1. Gebruik de couponcode voor de winkelregel die u in stap 3 hebt gemaakt.

<u>Verwachte resultaten</u>:

Er wordt geen korting toegepast op het winkelwagentje.

<u>Werkelijke resultaten</u>:

Korting wordt toegepast op het winkelwagentje.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
