---
title: 'ACSD-52736: [!UICONTROL Cart Price Rule] werkt niet zoals verwacht'
description: Pas de ACSD-52736-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een [!UICONTROL Cart Price Rule] die de vereisten voor configureerbare producthoeveelheid bevat, niet werkt zoals u had verwacht.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] werkt niet zoals verwacht

De ACSD-52736-patch verhelpt het probleem dat een [!UICONTROL Cart Price Rule] die de vereisten voor configureerbare producthoeveelheid bevat, niet naar behoren functioneert. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 wordt geïnstalleerd. De patch-id is ACSD-52736. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een [!UICONTROL Cart Price Rule] die de vereisten voor configureerbare producthoeveelheid omvat, werkt niet zoals verwacht.

<u> Stappen om </u> te reproduceren:

1. Een winkelwagentregel maken:
   * [!UICONTROL Apply] = Percentage van korting op productprijs
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Pas de regel alleen toe op de winkelwagentjes die aan de volgende voorwaarden voldoen: hoeveelheid in winkelwagentje is 1
2. Voeg een product met [!UICONTROL Qty] = 2 toe aan het winkelwagentje.
3. Controleer de prijzen van winkelwagentjes.

<u> Verwachte resultaten </u>:

De regel wordt niet toegepast omdat de hoeveelheid producten in de kar *2* is.

<u> Ware resultaten </u>:

De korting wordt toegepast.

<u> Aanvullende stappen vereist na de patch-installatie </u> :

Na het toepassen van het flard, moeten de voorwaarden van de kartregel gebruikend het *attribuut van de Hoeveelheid* worden verwijderd en opnieuw toegevoegd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
