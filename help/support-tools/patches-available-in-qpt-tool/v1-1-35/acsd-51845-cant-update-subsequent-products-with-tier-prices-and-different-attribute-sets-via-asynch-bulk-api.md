---
title: "ACSD-51845: Kan volgende producten met laagprijzen en verschillende kenmerksets niet bijwerken via asynch bulk  [!DNL API]"
description: Pas ACSD-51845 flard toe om de kwestie van Adobe Commerce te bevestigen waar u geen verdere producten met laagprijzen en verschillende attributenreeksen via asynchrone bulk  [!DNL REST API] kunt bijwerken.
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845: Kan volgende producten met prijzen op lagen en verschillende kenmerksets niet bijwerken via asynch bulksgewijs [!DNL API]

De ACSD-51845-patch verhelpt het probleem dat u volgende producten met prijzen op lagen en verschillende kenmerksets niet via asynchrone bulksgewijs kunt bijwerken [!DNL REST API]. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-51845. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Update mislukt voor volgende producten met laagprijzen en verschillende kenmerksets via asynchrone bulksgewijs [!DNL REST API] .

<u> Stappen om </u> te reproduceren:

1. Configureer [!DNL RabbitMQ].
1. Maak twee kenmerkensets.
1. Creeer twee **Eenvoudige Producten**, toewijzend elk product aan een verschillende geplaatste attributen.
1. Voeg de Prijs van de Groep van de a **Klant** voor elk product toe.
1. Werk beide producten bij in dezelfde bulkupdate van [!DNL API] .
1. Controleer of de opdracht `bin/magento queue:consumers:start async.operations.all` wordt uitgevoerd.
1. Controleer de status van het bulkbestand [!DNL API] .

<u> Verwachte resultaten </u>:

De service is uitgevoerd.

<u> Ware resultaten </u>:

Het systeem keert de foutenmelding terug: *het product kon niet worden bewaard. Probeer het opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
