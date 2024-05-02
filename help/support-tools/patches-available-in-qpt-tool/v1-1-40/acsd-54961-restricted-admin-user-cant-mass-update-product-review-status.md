---
title: "ACSD-54961: gebruikers met beperkte beheerdersrechten kunnen geen massaupdate uitvoeren [!UICONTROL Product Review status]"
description: Pas de ACSD-54961-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een gebruiker met beperkte bevoegdheden de status Product Review niet massaal kan bijwerken.
feature: Products
role: Admin, Developer
exl-id: 26c5bacd-21de-4533-a7b6-4acbacd38fec
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54961: gebruikers met beperkte beheerdersrechten kunnen geen massaupdate uitvoeren [!UICONTROL Product Review status]

De ACSD-54961-patch verhelpt het probleem waarbij een gebruiker met beperkte bevoegdheden geen massale update kan uitvoeren [!UICONTROL Product Review status]. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 is geïnstalleerd. De patch-id is ACSD-54961. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een gebruiker met beperkte beheerdersrechten kan geen update massaal uitvoeren [!UICONTROL Product Review status].

<u>Stappen om te reproduceren</u>:

1. Maak een aanvullende website-, opslag- en winkelweergave.
1. Voeg een product toe aan de tweede winkel en voeg vervolgens een revisie toe.
1. Creeer een beperkte admin gebruiker met toegang tot slechts de tweede opslag.
1. Meld u aan als gebruiker met beperkte beheerdersrechten en ga vervolgens naar **[!UICONTROL  Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]** en stelt de **Status** tot *Goedgekeurd* of *In behandeling*.

<u>Verwachte resultaten</u>:

De beperkte admin-gebruiker kan revisies bijwerken met de functie **[!UICONTROL Mass Update]** handeling.

<u>Werkelijke resultaten</u>:

Er is een fout opgetreden tijdens het bijwerken van revisies met **[!UICONTROL Mass Update]** handeling.<br>
De `var/log/exception.log` bevat een vergelijkbare fout:

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
