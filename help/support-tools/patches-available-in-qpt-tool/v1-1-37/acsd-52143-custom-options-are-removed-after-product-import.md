---
title: 'ACSD-52143: aangepaste opties worden verwijderd na het importeren van het product'
description: Pas de ACSD-52143-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de aanpassingsopties worden verwijderd nadat het product is geïmporteerd.
feature: Data Import/Export
role: Admin, Developer
exl-id: 7dde1efe-37a3-443f-9ce1-82cf1b3d9da7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-52143: na het importeren van het product worden de aangepaste opties verwijderd

De ACSD-52143-patch verhelpt het probleem waarbij de aangepaste opties worden verwijderd na het importeren van het product. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 wordt geïnstalleerd. De patch-id is ACSD-52143. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De aangepaste opties worden verwijderd nadat het product is geïmporteerd.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Store]** > **[!UICONTROL All Stores]** en stel een instantie van meerdere winkels in (één website met twee winkelweergaven).
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en maak twee producten met [!UICONTROL Customizable Options] .
1. Voeg in elk product een [!UICONTROL Customizable Option] toe.
1. Schakel over naar de tweede winkelweergave en wijzig de productnaam op elk product.
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** en exporteer de twee producten die u hebt gemaakt.
1. Download het CSV-bestand.
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** en importeer het bestand opnieuw.
1. Controleer beide producten.

<u> Verwachte resultaten </u>:

De aangepaste opties worden niet verwijderd nadat het product is geïmporteerd.

<u> Ware resultaten </u>:

De douaneopties worden verwijderd na de invoer van het product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
