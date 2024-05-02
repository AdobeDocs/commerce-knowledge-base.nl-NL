---
title: 'ACSD-47937: meldingen voor prijsdaling zijn niet verzonden vanwege caching op toepassingsniveau'
description: Pas de ACSD-47937-patch toe om het Adobe Commerce-probleem op te lossen, waarbij prijsdalingsmeldingen niet altijd worden verzonden als gevolg van caching op toepassingsniveau.
exl-id: f39c9ef6-4689-427f-bd61-3a52dec88be2
feature: Admin Workspace, Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-47937: meldingen voor prijsdaling zijn niet verzonden vanwege caching op toepassingsniveau

De ACSD-47937-patch verhelpt het probleem dat prijsdalingsmeldingen niet altijd worden verzonden vanwege caching op toepassingsniveau. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 is geïnstalleerd. De patch-id is ACSD-47937. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 en 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4, 2.4.5 en 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klanten krijgen geen e-mail met prijsverlaging voor producten voor latere prijswijzigingen.

<u>Stappen om te reproduceren</u>:

1. Inschakelen **[!UICONTROL Product Alert]** voor beide *[!UICONTROL Price Changes]* en *[!UICONTROL Back in Stock]* in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. Inschakelen **[!UICONTROL Display Out of Stock Products]**.
1. Maak een eenvoudig product (ABC) met qty = 0.
1. Maak een klant van de winkel en meld u aan voor het bovenstaande product om productwaarschuwingen voor prijsdalingen te ontvangen.
1. Start de productwaarschuwing voor klanten.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Verlaag de prijs voor het ABC-product.
1. Trigger de waarschuwing voor het product.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Verlaag de prijs voor het ABC-product opnieuw.
1. Trigger de waarschuwing voor het product.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Als u niet vertrouwd bent met [!DNL n98] kan worden uitgevoerd `bin/magento cron:run command` zoals gebruikelijk en `cron_schedule` tabel om te controleren `catalog_product_alert` de baan krijgt successtatus.

<u>Verwachte resultaten</u>:

De tweede e-mail voor prijsverlaging wordt verzonden.

<u>Werkelijke resultaten</u>:

De tweede e-mail voor prijsverlaging wordt niet verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
