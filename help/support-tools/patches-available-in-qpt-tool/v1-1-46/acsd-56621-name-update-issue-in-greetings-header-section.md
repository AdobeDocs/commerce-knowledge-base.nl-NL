---
title: 'ACSD-56621: Bijgewerkte namen worden niet weergegeven in de begroetingheader voor de gebruiker van het bedrijfsbeheer'
description: Pas de ACSD-56621-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de bijgewerkte voornaam en achternaam van de beheerder van het bedrijf niet worden weergegeven in de sectie met begroetingkoppen.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 4ad9c878-b617-4e6a-939c-be15faf7124b
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56621: Bijgewerkte namen worden niet weergegeven in de begroetingheader voor de gebruiker van het bedrijfsbeheer

De ACSD-56621-patch verhelpt het probleem waarbij de bijgewerkte voornaam en achternaam van de beheerder van het bedrijf niet in de sectie van de begroetingsheader worden weergegeven. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 wordt geïnstalleerd. De patch-id is ACSD-56621. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De bijgewerkte namen worden niet weergegeven in de begroetingheader voor gebruikers van bedrijfs-admin.

<u> Stappen om </u> te reproduceren:

1. Navigeer naar het deelvenster **[!UICONTROL Admin]** .
1. Ga naar **[!UICONTROL Stores]** en selecteer **[!UICONTROL Configuration]** .
1. Selecteer onder de sectie **[!UICONTROL General]** de optie **[!UICONTROL B2B]** om de functionaliteit van het B2B-bedrijf in te schakelen.
1. Ga naar **[!UICONTROL Storefront]** en registreer een nieuw bedrijf.
1. Meld u aan als de beheerder van het bedrijf.
1. Ga naar **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** en wijzig de velden voor de voornaam en achternaam naar wens.

<u> Verwachte resultaten </u>:

De voornaam en achternaam van de gebruiker in de sectie van de begroetingsheader worden onmiddellijk gewijzigd.

<u> Ware resultaten </u>:

De voor- en achternaam van de gebruiker worden alleen gewijzigd wanneer de gebruiker zich afmeldt en zich opnieuw aanmeldt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
