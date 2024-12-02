---
title: 'ACSD-51114: Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld'
description: Pas het ACSD-51114-patch toe om de Adobe Commerce-uitgave te corrigeren. Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld.
exl-id: 6ea7de32-1d30-4c4a-af6e-6a0931396846
feature: Catalog Management, Categories, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51114: Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld

>[!NOTE]
>
>Deze patch is vervangen.

De markering ACSD-51114 verhelpt de producten van de kwestie Willekeurige verdwenen uit grote catalogi wanneer het asynchrone indexeren wordt toegelaten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 wordt geïnstalleerd. De patch-id is ACSD-5114. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool]:pagina Patches zoeken].Gebruik de patch-id als een zoektrefwoord om de patch te zoeken.

## Probleem

Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Maak een set van 10 producten.
1. Stel alle indexen in op de modus **[!UICONTROL Update on Save]** .
1. Maak een categorie en wijs er alle producten aan toe.
1. Alle producten uitschakelen.
1. Open de categorie en controleer of er geen producten zijn.
1. Stel alle indexen in op de modus **[!UICONTROL Update on Schedule]** .
1. Stel de `DEFAULT_BATCH_SIZE` in op 2 in `lib/internal/Magento/Framework/Mview/View.php#L31` .
1. Laat producten in de volgende orde toe: 1st, 9th, 2nd, 5th, 10th, 3rd.
1. Uitsnijden uitvoeren, opdracht.
1. Open de rubriek opnieuw.

<u> Verwachte resultaten </u>:

Alle ingeschakelde producten worden weergegeven.

<u> Ware resultaten </u>:

Alle toegelaten producten worden niet getoond.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
