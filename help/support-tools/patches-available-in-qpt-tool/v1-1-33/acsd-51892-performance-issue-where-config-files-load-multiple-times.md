---
title: 'ACSD-51892: Prestatieprobleem waarbij configuratiebestanden meerdere keren worden geladen'
description: Pas de ACSD-51892-patch toe om het probleem met de Adobe Commerce-prestaties op te lossen, waarbij configuratiebestanden tijdens de implementatie meerdere keren worden geladen.
feature: Observability
role: Admin
exl-id: 397343df-360f-43c4-bcef-be5f0da5aeef
source-git-commit: 97734799a39f41d0d6441379e21608fa5fcd1d4c
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-51892: Prestatieprobleem waarbij configuratiebestanden meerdere keren worden geladen

De ACSD-51892-patch verhelpt het prestatieprobleem dat optreedt bij het laden van de `app/etc/env.php` en `app/etc/config.php` bestanden elke keer dat implementatieconfiguratiewaarden worden benaderd binnen één aanvraag. Door de te grote aflezing van bestanden wordt het systeem onder druk gezet, wat de algehele prestaties nadelig beïnvloedt. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51892. De kwestie is opgelost in Adobe Commerce 2.4.6-p2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er is een prestatieprobleem waarbij de configuratiebestanden meerdere keren worden geladen.

<u>Stappen om te reproduceren</u>:

1. Voer implementatie of upgrade uit naar Adobe Commerce 2.4.6 of hoger.
1. Controleer de bestandssysteemlogboeken voor toegang tot `app/etc/env.php` en `app/etc/config.php` bestanden tijdens de implementatie.

<u>Verwachte resultaten</u>:

Implementatie is voltooid binnen de normale tijdsperiode.

<u>Werkelijke resultaten</u>:

* De servers hebben moeite om te reageren op opdrachten die u invoert. Dit leidt tot *Fout 503 eerste byte timeout* wanneer u de website opent.
* Er staan meerdere items in logbestanden die toegang hebben tot `app/etc/env.php` en `app/etc/config.php` bestanden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
