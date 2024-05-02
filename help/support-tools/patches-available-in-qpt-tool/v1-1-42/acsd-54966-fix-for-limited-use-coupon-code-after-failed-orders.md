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

De ACSD-54966-patch verhelpt het probleem dat het hergebruik van couponcodes die per klant zijn beperkt, niet mogelijk is na een eerder mislukte bestelling. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 is geïnstalleerd. De patch-id is ACSD-54966. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een couponcode, beperkt voor eenmalig gebruik per klant, kan niet opnieuw worden gebruikt na een mislukte vorige bestelling.

<u>Stappen om te reproduceren</u>:

1. Een regel voor een winkelwagenprijs instellen met *[!UICONTROL Uses per Customer]* = *1*.
1. Ga door met een aankoop met de toegewezen couponcode.
1. Annuleer de bestelling via het beheerpaneel of voer de bestelling uit met een betalingsfout.
1. Voer de opdracht uit: `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Probeer een volgende bestelling te plaatsen met dezelfde couponcode voor dezelfde klant.

<u>Verwachte resultaten</u>:

Nadat de bestelling is geannuleerd of een betalingsfout is opgetreden, kan de klant de couponcode opnieuw gebruiken voor een nieuwe aankoop.

<u>Werkelijke resultaten</u>:

De klant kan de couponcode niet opnieuw gebruiken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
