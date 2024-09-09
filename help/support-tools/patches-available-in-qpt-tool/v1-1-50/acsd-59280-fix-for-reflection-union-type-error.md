---
title: '"ACSD-59280: "ReflectionUnionType::getName()"-fout in 2.4.4-pX-installaties"'
description: Pas de ACSD-59280-patch toe om het Adobe Commerce-probleem te verhelpen waarbij de fout 'call to undefined method RefCollectionUnionType::getName()' optreedt tijdens de installatie van 2.4.4-pX-versies.
feature: Install, Upgrade
role: Admin, Developer
source-git-commit: a7a42520c6c7d74e995d104271afa2b15b537de7
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-59280: `ReflectionUnionType::getName()` fout in 2.4.4-pX-installaties

De ACSD-59280-patch verhelpt het probleem waarbij de `call to undefined method ReflectionUnionType::getName()` -fout optreedt tijdens de installatie van 2.4.4-pX-versies. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-59280. De kwestie is opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`ReflectionUnionType::getName()` fout tijdens installatie 2.4.4-pX.

<u> Stappen om </u> te reproduceren:

Voer een nieuwe installatie uit met *[!UICONTROL Composer]* .

<u> Verwachte resultaten </u>:

Het installatieproces wordt zonder fouten voltooid.

<u> Ware resultaten </u>:

De volgende fout wordt tijdens het `setup:upgrade` -proces weergegeven:

`Call to undefined method ReflectionUnionType::getName()`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
