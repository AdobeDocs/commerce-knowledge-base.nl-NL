---
title: 'ACSD-49480: achtereenvolgende regels negeren die niet werken'
description: Pas de ACSD-49480-patch toe om het Adobe Commerce-probleem op te lossen waarbij [!UICONTROL Cart Price Rule - Discard Subsequent Rules] niet naar behoren werkt.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] werkt niet zoals verwacht

De ACSD-49480-patch verhelpt het probleem waarbij [!UICONTROL Cart Price Rule - Discard Subsequent Rules] niet naar behoren werkt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-49480. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] werkt niet zoals bedoeld.

<u> Stappen om </u> te reproduceren:

1. Creeer a **[!UICONTROL Cart Price Rule]** met een couponcode (noem het als *TEST*) die een korting $10 aan *identiteitskaart van het Product 1* in het **[!UICONTROL Actions]** lusje met [!UICONTROL Discard Subsequent Rules] geeft die aan *[!UICONTROL Yes]* wordt geplaatst en [!UICONTROL Priority] aan *1* wordt geplaatst.
1. Creeer een andere **[!UICONTROL Cart Price Rule]** zonder een couponcode die een korting $5 aan *identiteitskaart van het Product 2* in het **[!UICONTROL Actions]** lusje met [!UICONTROL Priority] geeft die aan *2* wordt geplaatst. Hier, veronderstellen wij, dit een globale verkoop voor *identiteitskaart 2 van het Product* is.
1. Ga naar frontend plaats en voeg *identiteitskaart van het Product 1* en *identiteitskaart van het Product 2* in de kar toe.
1. Pas de ** couponcode van de TEST toe.

<u> Verwachte resultaten </u>

* *Korting 1* wordt toegepast op *identiteitskaart 1 van het Product*.
* *Korting 2* wordt toegepast op *identiteitskaart van het Product 2*.

<u> Ware resultaten </u>

* Slechts *Korting 1* wordt toegepast op *identiteitskaart 1 van het Product*.
* *Korting 2* wordt niet toegepast op *identiteitskaart van het Product 2*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
