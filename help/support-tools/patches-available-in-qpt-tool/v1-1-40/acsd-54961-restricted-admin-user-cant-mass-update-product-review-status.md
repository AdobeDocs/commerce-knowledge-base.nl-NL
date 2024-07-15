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

De ACSD-54961-patch verhelpt het probleem waarbij een gebruiker met beperkte beheerdersrechten geen massale update kan uitvoeren [!UICONTROL Product Review status] . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 wordt geïnstalleerd. De patch-id is ACSD-54961. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een gebruiker met beperkte beheerdersrechten kan geen massale update uitvoeren [!UICONTROL Product Review status] .

<u> Stappen om </u> te reproduceren:

1. Maak een aanvullende website-, opslag- en winkelweergave.
1. Voeg een product toe aan de tweede winkel en voeg vervolgens een revisie toe.
1. Creeer een beperkte admin gebruiker met toegang tot slechts de tweede opslag.
1. Login als beperkte admin gebruiker, ga dan naar **[!UICONTROL  Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]**, en plaats de **Status** aan *Goedgekeurd* of *Hangende*.

<u> Verwachte resultaten </u>:

De gebruiker met beperkte beheerdersrechten kan revisies bijwerken met de handeling **[!UICONTROL Mass Update]** .

<u> Ware resultaten </u>:

Er treedt een fout op bij het bijwerken van revisies met behulp van de handeling **[!UICONTROL Mass Update]** .<br>
`var/log/exception.log` bevat een vergelijkbare fout:

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
