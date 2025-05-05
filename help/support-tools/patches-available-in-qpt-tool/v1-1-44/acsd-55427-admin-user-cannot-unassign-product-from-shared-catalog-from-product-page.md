---
title: 'ACSD-55427: een beheerder kan het toewijzen van een product niet ongedaan maken via **[!UICONTROL Product in Shared Catalogs]** op de productpagina'
description: Pas de ACSD-55427-patch toe om het Adobe Commerce-probleem op te lossen waarbij de toewijzing van een product niet ongedaan kan worden gemaakt vanaf **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427: een beheerder kan de toewijzing van het product aan **[!UICONTROL Product in Shared Catalogs]** op de productpagina niet ongedaan maken

De ACSD-55427-patch verhelpt het probleem dat u de toewijzing van een product uit **[!UICONTROL Product in Shared Catalogs]** op de productpagina in de catalogus in Commerce Admin niet ongedaan kunt maken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 wordt geïnstalleerd. De patch-id is ACSD-55427. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

U kunt de toewijzing van een product uit **[!UICONTROL Product in Shared Catalogs]** op de productpagina in de catalogus in Commerce Admin niet ongedaan maken.

<u> Stappen om </u> te reproduceren:

Vereisten: Adobe Commerce geïnstalleerd met zowel B2B als **[!UICONTROL Shared Catalogs]** ingeschakeld.
1. Maak een product.
1. Navigeer naar het gedeelde catalogusdashboard en open de standaard gedeelde catalogus.
1. Het product toewijzen aan de standaardcatalogus en een lagere prijs dan de productprijs instellen.
1. Sla de gedeelde catalogus op.
1. Voer de [!UICONTROL CRON] uit om de consumenten/indexen bij te werken.
1. Open het product en verwijder het product onder **[!UICONTROL Product in Shared Catalogs]** -sectie.

<u> Verwachte resultaten </u>:

Het product moet onder **[!UICONTROL Product in Shared Catalogs]** -sectie worden verwijderd.

<u> Ware resultaten </u>:

Het product wordt nog steeds weergegeven in de sectie **[!UICONTROL Product in Shared Catalogs]** .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
