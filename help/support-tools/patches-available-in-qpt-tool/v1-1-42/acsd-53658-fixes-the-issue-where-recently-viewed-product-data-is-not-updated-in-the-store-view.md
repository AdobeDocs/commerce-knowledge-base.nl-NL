---
title: 'ACSD-53658: **[!UICONTROL Recently Viewed Product]** gegevens niet correct bijgewerkt in winkelweergave'
description: Pas de ACSD-53658-patch toe om het Adobe Commerce-probleem op te lossen, waarbij **[!UICONTROL Recently Viewed Product]** gegevens niet correct worden bijgewerkt in de winkelweergave.
feature: CMS, Personalization
role: Admin, Developer
exl-id: 4086dcee-37e5-4393-9048-ce19a2d248e9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]** gegevens worden niet correct bijgewerkt in de winkelweergave

De ACSD-53658-patch verhelpt het probleem waarbij **[!UICONTROL Recently Viewed Product]** -gegevens niet correct worden bijgewerkt in de winkelweergave. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-53658. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De **[!UICONTROL Recently Viewed Product]** -gegevens worden niet correct bijgewerkt in de winkelweergave.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij het deelvenster Beheer.
1. Maak een tweede opslagweergave voor de standaardwebsite.
1. Maak een eenvoudig product.
1. Stel een andere productnaam in voor de nieuwe winkelweergave.
1. Maak een **[!UICONTROL Recently Viewed Product]** -widget.
1. Configureer deze widget voor weergave op de startpagina.
1. Open de productpagina in de Storefront vanuit de standaardwinkelweergave.
1. Open de startpagina.
1. Schakel over naar de tweede winkelweergave met de opslagschakelaar.

<u> Verwachte resultaten </u>:

De productnaam wordt bijgewerkt in de widget.

<u> Ware resultaten </u>:

De productnaam wordt niet bijgewerkt in de widget.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
