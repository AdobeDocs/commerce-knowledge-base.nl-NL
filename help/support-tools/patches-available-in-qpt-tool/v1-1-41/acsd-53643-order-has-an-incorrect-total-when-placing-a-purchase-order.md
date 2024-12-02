---
title: 'ACSD-53643: het totaal van een bestelling is onjuist bij het plaatsen van een inkooporder'
description: Pas de ACSD-53643-patch toe om het Adobe Commerce-probleem op te lossen waarbij het totaal van de bestelling onjuist is wanneer een inkooporder wordt geplaatst met uitgeschakelde of out-of-stock producten.
feature: B2B
role: Admin, Developer
exl-id: 9843e07a-8a17-401e-98bc-559df5148d34
source-git-commit: 2356ac10b05ae9f38e5c0ca90d9156b0fc405718
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643: het totaal van een bestelling is onjuist bij het plaatsen van een inkooporder

De ACSD-53643-patch verhelpt het probleem waarbij het totaal van de bestelling onjuist is bij het plaatsen van een inkooporder met uitgeschakelde of out-of-stock producten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 wordt geïnstalleerd. De patch-id is ACSD-53643. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het totaal van de bestellingen is onjuist wanneer u een inkooporder plaatst met een product dat uit de oorspronkelijke voorraad of een handicap bestaat.

<u> Stappen om </u> te reproduceren:

1. Installeer *[!UICONTROL B2B]* en *[!UICONTROL Inventory]* .
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** en reeks **[!UICONTROL Company]** = *ja* en **[!UICONTROL Purchase Order]** = *ja*.
1. Wis configuratiecache.
1. Maak een nieuw bedrijf, activeer het en schakel *[!UICONTROL Purchase order]* in voor het bedrijf.
1. Maak een nieuwe gebruiker voor het bedrijf.
1. Creeer een *regel van de Goedkeuring* om alle orden van meer dan *1 USD* door de bedrijfbeheerder goed te keuren.
1. Maak een extra bron.
1. Meld u aan als nieuwe bedrijfgebruiker.
1. Voeg twee producten aan de kar toe en plaats een kooporder.
1. Schakel het tweede product uit.
1. Meld u aan als bedrijfsbeheerder.
1. Open de kooporder en controleer of de kooporder zowel producten bevat als het totaal voor beide producten.
1. Goedkeuren van de kooporder.
1. Plaats de bestelling.
1. Open de bestelgegevens.

<u> Verwachte resultaten </u>:

* Kan de orde plaatsen zelfs als één product in de orde *gehandicapt* of *uit voorraad* is.
* *[!UICONTROL Place Order]* verborgen.

<u> Ware resultaten </u>:

De geplaatste order bevat alleen het eerste actieve product, maar het totale ordervolume wordt voor beide producten berekend.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
