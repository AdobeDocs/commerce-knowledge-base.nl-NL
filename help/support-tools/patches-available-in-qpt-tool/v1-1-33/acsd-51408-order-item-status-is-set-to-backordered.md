---
title: 'ACSD-51408: de status van het orderitem is onjuist ingesteld op [!UICONTROL backordered]'
description: Pas de ACSD-51408-patch toe om het Adobe Commerce-probleem op te lossen waarbij de status van het orderitem onjuist is ingesteld op [!UICONTROL backordered] .
feature: B2B, Orders
role: Admin
exl-id: 0355beca-4612-438f-8f91-be42d8d637e9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# ACSD-51408: de status van een Order-item is onjuist ingesteld op *[!UICONTROL backordered]*

De ACSD-51408-patch verhelpt het probleem waarbij de status van het orderitem onjuist is ingesteld op [!UICONTROL backordered] . Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51408. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van het orderitem wordt onjuist ingesteld op *[!UICONTROL backordered]* .

<u> Eerste vereisten </u>:

Adobe Commerce B2B- en Inventory management-modules (MSI) zijn geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe website, sla deze op en sla de weergave op.
1. Maak een nieuwe bron.
1. Maak een nieuw bestand dat is gekoppeld aan de nieuwe website die in stap 1 is gemaakt en wijs de bron toe die in stap 2 is gemaakt.
1. Maak een bedrijf en wijs het toe aan de nieuwe website die in stap 1 wordt gemaakt.
1. Creeer een nieuwe klant en wijs het aan het bedrijf toe dat in stap 4 wordt gecreeerd.
1. Creeer een product, wijs het aan de nieuwe website toe, en plaats **[!UICONTROL default stock]** = *0*, en **[!UICONTROL new stock]** aan groter dan *0*.
1. Schakel **[!UICONTROL backorders]** in.
1. Schakel **[!UICONTROL Check/Money Order]** -betalingsmethode in voor het nieuwe websitebereik.
1. Schakel **[!UICONTROL Flat Rate shipping method]** in voor nieuw websitebereik.
1. Maak een nieuwe volgorde via **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** .
1. Selecteer de nieuwe klant die u in stap 5 hebt gemaakt.
1. Selecteer de nieuwe winkel die u in stap 1 hebt gemaakt.
1. Kies het product dat u in stap 6 hebt gemaakt.
1. Vul de bestelgegevens in, inclusief de betaling- en verzendmethoden.
1. Verzend de bestelling.
1. Controleer de *Status van het Punt*.

<u> Verwachte resultaten </u>

Het object kan uit de voorraad worden verzonden. De status van het item is *[!UICONTROL ordered]* .

<u> Ware resultaten </u>

De status van het item is *[!UICONTROL backordered]* .

>[!MORELIKETHIS]
>
>[ het puntstatus van de Orde wordt verkeerd geplaatst aan *[!UICONTROL Ordered]* wanneer de productvoorraad 0 is.](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
