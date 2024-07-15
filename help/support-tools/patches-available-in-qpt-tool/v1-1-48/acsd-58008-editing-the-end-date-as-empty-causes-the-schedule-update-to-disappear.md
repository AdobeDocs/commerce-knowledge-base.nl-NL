---
title: 'ACSD-58008: Het uitgeven van de einddatum als *empty* veroorzaakt de programmaupdate om te verdwijnen'
description: Pas de ACSD-58008-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het bewerken van de einddatum als *empty* ertoe leidt dat de update van het schema verdwijnt.
feature: Staging, Page Content
role: Admin, Developer
exl-id: bfa590b8-377b-49dd-9aff-f89b8fd815c4
source-git-commit: d7ace1f20defb01105d4a241f971b06fca052215
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008: Het uitgeven van de einddatum zoals *leeg* veroorzaakt de planningupdate om te verdwijnen

ACSD-58008 herstelt de flard waar het uitgeven van de einddatum zoals *leeg* de planningsupdate veroorzaakt om te verdwijnen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-58008. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het uitgeven van de einddatum als *leeg* veroorzaakt de planningupdate om te verdwijnen

<u> Stappen om </u> te reproduceren:

1. Meld u aan als [!UICONTROL Admin] .
1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** en maak een pagina.
1. Selecteer de gemaakte pagina en klik op **[!UICONTROL Schedule New Update]** . *(Navigeer het op de hoogste juiste hoek van de pagina)*.
1. Maak vier updates. *(Bijvoorbeeld, als toename van* 2 *notulen)*.
1. Werk *update 2* bij en verander de tijd in een tijd die vóór laatste *update 4* is.
1. Sla de aangebrachte updates op.

<u> Verwachte resultaten </u>:

De planningupdate toont *update 3*.

<u> Ware resultaten </u>:

De programma update toont niet *update 3*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
