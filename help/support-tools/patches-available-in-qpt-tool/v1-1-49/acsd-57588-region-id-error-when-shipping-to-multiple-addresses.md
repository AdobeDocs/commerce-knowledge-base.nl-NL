---
title: 'ACSD-57588: Fout bij verwerken van regio-id bij verzending naar meerdere adressen'
description: Pas de ACSD-57588-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het verzenden van een bestelling naar meerdere adressen een fout veroorzaakt tijdens de verwerking van de regio-id.
feature: Orders, Shipping/Delivery
role: Admin, Developer
exl-id: 01a33db3-fdbe-4acd-a617-45fb3aee6f3d
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-57588: Fout bij verwerken van regio-id bij verzending naar meerdere adressen

De ACSD-57588-patch verhelpt het probleem waarbij het verzenden van een bestelling naar meerdere adressen een fout veroorzaakt tijdens de verwerking van regio-id&#39;s. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 wordt geïnstalleerd. De patch-id is ACSD-57588. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Fout tijdens verwerken van regio-id bij verzending naar meerdere adressen.

<u> Stappen om </u> te reproduceren:

1. Configureer de betalingsmethode [!DNL Braintree] .
1. Meld u aan als klant op de winkel.
1. Voeg een product toe aan het winkelwagentje en ga door met het bekijken en bewerken van het winkelwagentje.
1. Voeg veelvoudige adressen *(bijvoorbeeld, VK, V.S., CA)* tijdens het controleproces toe en herzie de orde.
1. Selecteer op de afhandelingspagina de optie voor creditcardbetaling, voer de benodigde gegevens in en plaats de bestelling.

<u> Verwachte resultaten </u>:

De bestelling kan met succes worden geplaatst.

<u> Ware resultaten </u>:

De volgorde wordt niet geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
