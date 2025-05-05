---
title: 'ACSD-60303: probleem met plaatsing van beheerbestellingen is opgelost waarbij HTML-miniatuur is ingeschakeld'
description: Pas de ACSD-60303-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een bestelling van Admin niet kan worden geplaatst als HTML minificatie is ingeschakeld.
feature: Orders
role: Admin, Developer
exl-id: 06f7fc4f-8cdc-47c6-a706-52b8e70d66e0
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-60303: probleem met plaatsing van beheerbestellingen is opgelost waarbij HTML-miniatuur is ingeschakeld

De ACSD-60303-patch verhelpt het probleem waarbij geen bestelling van Admin kan worden geplaatst als de miniatuur van de HTML is ingeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-60303. De kwestie wordt volgens de planning in 2.4.8 opgelost.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p9 - 2.4.4-p10, 2.4.5-p8 - 2.4.5-p9, 2.4.6-p6 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bestellingen kunnen niet vanuit het deelvenster Beheer worden geplaatst wanneer de miniatuur HTML is ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Schakel miniaturen van HTML in.
1. Stel de waarde **[!UICONTROL Application Mode]** in op *[!UICONTROL Production]* .
1. Maak een volgorde in het deelvenster Beheer.

<u> Verwachte resultaten </u>:

De bestelling is geplaatst.

<u> Ware resultaten </u>:

De volgorde wordt niet gemaakt en de volgende fout wordt geregistreerd:

`report.CRITICAL: ParseError: syntax error, unexpected token "<<" in var/view_preprocessed/pub/static/vendor/magento/module-gift-wrapping/view/adminhtml/templates/order/create/info.phtml:1`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
