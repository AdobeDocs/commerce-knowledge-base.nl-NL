---
title: 'ACSD-48448: Uitgave van de zeldzame omstandigheid tijdens annuleringen van orders die leiden tot dubbele opname in de voorraad_reserveringstabel'
description: Pas de ACSD-48448-patch toe om het Adobe Commerce-prestatieprobleem op te lossen, waarbij het probleem met de zeldzame omstandigheid optreedt tijdens het annuleren van de bestelling, wat leidt tot dubbele vermeldingen in de voorraad_reserveringstabel.
feature: Orders, Checkout
role: Admin
exl-id: 69d00219-bc9f-4531-9e85-38476c2258ed
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-48448: *[!UICONTROL Race]* probleem met omstandigheid tijdens orderannuleringen die dubbele invoer in `inventory_reservation` -tabel veroorzaken

De ACSD-48448-patch verhelpt het probleem waarbij het probleem met de voorwaarde *[!UICONTROL Race]* zich voordoet tijdens annuleringen van orders. Dit veroorzaakt dubbele vermeldingen in de `inventory_reservation` -tabel. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.34 is geïnstalleerd. De patch-id is ACSD-48448. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2 en 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er is een probleem met de voorwaarde *[!UICONTROL Race]* opgetreden tijdens annuleringen van orders, waardoor dubbele items in de `inventory_reservation` -tabel worden veroorzaakt.

<u> Stappen om </u> te reproduceren:

1. Plaats een bestelling.
1. Controleer de tabel `inventory_reservation` om er zeker van te zijn dat er een record is voor de gebeurtenis `order_placed` .
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

<u> Verwachte resultaten </u>:

Records worden niet gedupliceerd.

<u> Ware resultaten </u>:

Dubbele records worden gemaakt in de `inventory_reservation` -tabel voor `order_canceled` .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
