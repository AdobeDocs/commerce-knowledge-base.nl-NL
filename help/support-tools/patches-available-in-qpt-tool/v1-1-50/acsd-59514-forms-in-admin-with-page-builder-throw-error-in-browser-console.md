---
title: 'ACSD-59514: Forms in Admin met  [!DNL Page Builder]  werpen fout in browser console'
description: Pas ACSD-59514 flard toe om de kwestie van Adobe Commerce te bevestigen waar de vormen in Admin met  [!DNL Page Builder]  de fout "[!DNL Page Builder] teruggeven voor 5 seconden zonder loslaten."werpen in de browserconsole nadat het formulier is verzonden, kunnen wijzigingen niet worden opgeslagen.
feature: Page Builder
role: Admin, Developer
exl-id: 4bb17d7b-9ea4-44c2-a42b-d0117e5f8f9a
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-59514: Forms in Admin met [!DNL Page Builder] fout bij genereren in browserconsole

De ACSD-59514-patch verhelpt het probleem dat de formulieren in Admin met [!DNL Page Builder] throw de fout *[!DNL Page Builder]gedurende 5 seconden renderen zonder vergrendelingen vrij te geven.* in de browserconsole na het verzenden van het formulier en wijzigingen kunnen niet worden opgeslagen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-59514. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Forms in Admin met [!DNL Page Builder] geeft de fout *[!DNL Page Builder]gedurende 5 seconden weer zonder vergrendelingen vrij te geven.* in de browserconsole na het verzenden van het formulier en wijzigingen kunnen niet worden opgeslagen.

<u> Eerste vereisten </u>:

Adobe Commerce [!DNL Page Builder] -modules worden geïnstalleerd en ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Open het deelvenster Beheer en klik op de knop [!UICONTROL Content] .
1. Selecteer het blok en bewerk het blok.
1. Wijzig de inhoud en klik op [!UICONTROL Save] .
1. Open de console en zie de foutenmelding.

<u> Verwachte resultaten </u>:

Het blok is opgeslagen.

<u> Ware resultaten </u>:

De lader stopt niet met draaien en het blok wordt niet opgeslagen. De volgende fout wordt weergegeven in de browserconsole:
*[!DNL Page Builder]rendeerde gedurende 5 seconden zonder vergrendelingen vrij te geven.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
