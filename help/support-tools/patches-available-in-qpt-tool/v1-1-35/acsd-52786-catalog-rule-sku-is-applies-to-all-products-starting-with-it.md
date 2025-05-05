---
title: 'ACSD-52786: De regel van de Catalogus *[!UICONTROL SKU is]* is op alle producten van toepassing die met SKU beginnen'
description: Pas ACSD-52786 flard toe om de kwestie van Adobe Commerce te bevestigen waar de voorwaarde van de catalogusregel *[!UICONTROL SKU is]* op alle producten van toepassing is die met bepaalde SKU beginnen.
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786: De regel van de Catalogus &quot;*[!UICONTROL SKU is]*&quot;is op alle producten van toepassing die met SKU beginnen

De ACSD-52786-patch verhelpt het probleem waarbij de voorwaarde van de catalogusregel *[!UICONTROL SKU is]* van toepassing is op alle producten die beginnen met de opgegeven SKU. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-52786. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De voorwaarde van de catalogusregel *[!UICONTROL SKU is]* is op alle producten van toepassing die met bepaalde SKU beginnen.

<u> Stappen om </u> te reproduceren:

1. Maak twee producten, een met SKU &quot;24&quot; en een ander met SKU &quot;24-MB01&quot;.
1. Navigeer naar **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]** .
1. Pas de volgende voorwaarde toe:
   * *[!UICONTROL If **&#x200B; ALLE &#x200B;** van deze voorwaarden is WAAR **&#x200B; **]*: *[!UICONTROL SKU is 24]*
1. Stel een kortingsbedrag in in handelingen.
1. Klik op **[!UICONTROL Save and Apply]**.
1. Cachegeheugen leegmaken.
1. Ga naar de winkel en controleer de prijs van 24 MB01.

<u> Verwachte resultaten </u>:

De catalogusregel wordt toegepast slechts op één enkel product met SKU gelijk aan 24.

<u> Ware resultaten </u>:

De voorwaarde van de catalogusregel *[!UICONTROL SKU is]* is op alle producten van toepassing die met bepaalde SKU beginnen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
