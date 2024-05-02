---
title: 'ACSD-48448: Uitgave van de zeldzame omstandigheid tijdens annuleringen van orders die leiden tot dubbele vermelding in voorraad_reserveringstabel'
description: Pas de ACSD-48448-patch toe om het Adobe Commerce-prestatieprobleem op te lossen, waarbij het probleem met de zeldzame omstandigheid optreedt tijdens het annuleren van de bestelling, wat leidt tot dubbele vermeldingen in de voorraad_reserveringstabel.
feature: Orders, Checkout
role: Admin
exl-id: 69d00219-bc9f-4531-9e85-38476c2258ed
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-4848: *[!UICONTROL Race]* probleem met voorwaarde tijdens annuleringen van bestellingen die dubbele invoer veroorzaken in `inventory_reservation` table

De ACSD-48448-patch verhelpt het probleem waarbij de *[!UICONTROL Race]* Het probleem met de voorwaarde doet zich voor tijdens annuleringen van orders, waardoor dubbele vermeldingen in het dialoogvenster `inventory_reservation` tabel. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.34 is geïnstalleerd. De patch-id is ACSD-48448. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2 en 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

*[!UICONTROL Race]* Het probleem met de voorwaarde doet zich voor tijdens annuleringen van orders, waardoor dubbele vermeldingen in het dialoogvenster `inventory_reservation` tabel.

<u>Stappen om te reproduceren</u>:

1. Plaats een bestelling.
1. Controleer de `inventory_reservation` om er zeker van te zijn dat er een record is voor de `order_placed` gebeurtenis.
1. Voer het bijgevoegde script uit om de volgorde parallel te annuleren (vergeet niet de URL en de orderID te wijzigen).

`bash cancel_order.sh`

```
#!/bin/bash
baseUrl=" "
orderId=3
token=$(curl --location --request POST "${baseUrl}rest/V1/integration/admin/token" \
 -H 'Content-Type: application/json' \
 -d '{
  "username": "admin",
  "password": "password"
}')
echo ${token//\"/}
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
 &
sleep 0.1;
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
wait
```

<u>Verwachte resultaten</u>:

Records worden niet gedupliceerd.

<u>Werkelijke resultaten</u>:

Er worden dubbele records gemaakt in het dialoogvenster `inventory_reservation` tabel voor `order_canceled`.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
