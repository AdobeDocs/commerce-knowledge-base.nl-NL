---
title: 'ACSD-48070: uitzondering tijdens het bewerken van een geplande update'
description: Pas de ACSD-48070-patch toe om het Adobe Commerce-probleem op te lossen waarbij een uitzondering wordt geactiveerd tijdens het bewerken van een geplande update.
feature: Catalog Management, Categories
role: Admin
exl-id: 047813e3-4659-4a94-9dd8-e3534387a890
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-48070: uitzondering tijdens het bewerken van een geplande update

De ACSD-48070-patch verhelpt het probleem waarbij een uitzondering wordt geactiveerd tijdens het bewerken van een geplande update. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-48070. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een uitzondering geactiveerd tijdens het bewerken van een geplande update.

<u> Stappen om </u> te reproduceren:

1. Open een categorie.
2. Maak een nieuwe **[!UICONTROL Scheduled Update]** en sla deze op.
3. Klik op **[!UICONTROL View/Edit]** in het gemaakte bestand **[!UICONTROL Scheduled Update]** .
4. Sla het bestand opnieuw op.

<u> Verwachte resultaten </u>

**[!UICONTROL Scheduled Update]** wordt opgeslagen.

<u> Ware resultaten </u>

Een fout komt voor: *fout: iets ging verkeerd terwijl het bewaren van Magento\Catalog\Api\Data\CategoryInterface.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
