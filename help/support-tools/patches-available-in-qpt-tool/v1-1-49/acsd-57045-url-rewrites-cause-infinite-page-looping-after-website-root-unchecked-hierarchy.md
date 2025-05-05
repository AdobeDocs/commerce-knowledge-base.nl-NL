---
title: 'ACSD-57045: URL herschrijft zorgt voor oneindige paginering nadat [!UICONTROL Website Root] is uitgeschakeld in [!UICONTROL Hierarchy]'
description: Pas de ACSD-57045-patch toe om het Adobe Commerce-probleem op te lossen, waarbij URL-herschrijvingen ertoe leiden dat een oneindige paginarand wordt herhaald nadat [!UICONTROL Website Root] is uitgeschakeld in [!UICONTROL Hierarchy] .
feature: CMS
role: Admin, Developer
exl-id: 9dca2d1a-3aef-41f0-b140-f3987003a5fd
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# ACSD-57045: URL herschrijft zorgt voor oneindige paginering nadat [!UICONTROL Website Root] is uitgeschakeld in [!UICONTROL Hierarchy]

De ACSD-57045-patch verhelpt het probleem waarbij URL-herschrijvingen ertoe leiden dat een oneindige paginering plaatsvindt nadat **[!UICONTROL Website Root]** is uitgeschakeld in **[!UICONTROL Hierarchy]** . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 wordt geïnstalleerd. De patch-id is ACSD-57045. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

URL herschrijft zorgt ervoor dat de pagina oneindig wordt herhaald nadat **[!UICONTROL Website Root]** is uitgeschakeld in **[!UICONTROL Hierarchy]** .

<u> Stappen om </u> te reproduceren:

1. Creeer een pagina van CMS genoemd *test-Ouder*.
1. Creeer een pagina genoemd *test-Kind*, en in de **[!UICONTROL Hierarchy]** sectie, uitgezocht **[!UICONTROL Website Root]** > **[!UICONTROL Parent]** en sparen.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** .
1. Er zijn twee nieuwe herschrijvingen:
   * De weg van het verzoek aan *test-Ouder* die aan *cms/page/view/page_id/ID_NUMBER_FOR_PAGE* richt
   * De weg van het verzoek aan *test-Kind* die aan *cms/page/view/page_id/ID_NUMBER_FOR_PAGE* richt
1. Bezoek de storefront en voeg *test-kind* aan URL toe. U moet de onderliggende pagina zien.
1. Doe het zelfde ding, maar voeg *test-ouder/test-kind/* aan URL toe en zie de zelfde pagina.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** en selecteer **[!UICONTROL Add URL Rewrite]** . Kies de volgende instellingen:
   * Type: *Douane*
   * De weg van het verzoek: *test-ouder/test-kind*
   * De weg van het doel: *test-kind*
   * Redirect Type: *Permanent (301)*
1. Bezoek de *test-ouder/test-kind* weg en u zou aan *test-kind* opnieuw moeten worden gericht.
1. Bewerk de onderliggende pagina (**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** > Onderliggend element kiezen en selecteer **[!UICONTROL Edit]** ).
1. Onder de **[!UICONTROL Hierarchy]** sectie, houd *test-Ouder* geselecteerd maar unselect **[!UICONTROL Website Root]** en bewaar.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** en merk op dat origineel *test-kind* aan *cms/page/view/page_id* redirect mist, en op dat punt wordt het vervangen door een weg die *test-kind* aan *test-ouder/test-kind* richt.
1. Bezoek de storefront en probeer om de *test-kind* pagina te bezoeken.

<u> Verwachte resultaten </u>:

De *test-kind* pagina wordt geopend.

<u> Ware resultaten </u>:

De *test-Kind* pagina wordt niet geopend. Browser probeert om de *test-ouder/test-kind* pagina in een oneindige lijn te openen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
