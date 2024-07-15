---
title: 'ACSD-54966: Corrigeren voor hergebruik van couponcodes na mislukte orders'
description: Pas de ACSD-54966-patch toe om het Adobe Commerce-probleem op te lossen, waardoor het hergebruik van couponcodes die beperkt zijn per promotie en winkelwagentje na een eerder mislukte bestelling, wordt voorkomen.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: 931cfe7a-30a3-4a7d-ada5-4e2d7084f3e1
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-54966: Corrigeren voor hergebruik van couponcodes na mislukte orders

De ACSD-54966-patch verhelpt het probleem dat het hergebruik van couponcodes die per klant zijn beperkt, niet mogelijk is na een eerder mislukte bestelling. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-54966. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een couponcode, beperkt voor eenmalig gebruik per klant, kan niet opnieuw worden gebruikt na een mislukte vorige bestelling.

<u> Stappen om </u> te reproduceren:

1. Opstelling een de prijsregel van de winkelwagentje met *[!UICONTROL Uses per Customer]* = *1*.
1. Ga door met een aankoop met de toegewezen couponcode.
1. Annuleer de bestelling via het beheerpaneel of voer de bestelling uit met een betalingsfout.
1. Voer de opdracht uit: `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Probeer een volgende bestelling te plaatsen met dezelfde couponcode voor dezelfde klant.

<u> Verwachte resultaten </u>:

Nadat de bestelling is geannuleerd of een betalingsfout is opgetreden, kan de klant de couponcode opnieuw gebruiken voor een nieuwe aankoop.

<u> Ware resultaten </u>:

De klant kan de couponcode niet opnieuw gebruiken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
