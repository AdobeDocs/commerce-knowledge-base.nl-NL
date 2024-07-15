---
title: 'ACSD-47669: Interne serverfout bij het importeren van producten met aanpasbare opties'
description: Pas de ACSD-47669-patch toe om het Adobe Commerce-probleem op te lossen waarbij een interne serverfout optreedt tijdens het importeren van producten met aanpasbare opties.
feature: Products
role: Admin, Developer
exl-id: 14afbd71-075a-4264-8da2-dbbd93f472a1
source-git-commit: 66e56b9ba31fd2c5d3f8a330f09d8e94df77b17d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47669: Interne serverfout bij het importeren van producten met aanpasbare opties

De ACSD-47669-patch verhelpt het probleem waarbij een interne serverfout optreedt tijdens het importeren van producten met aanpasbare opties. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.38 wordt geïnstalleerd. De patch-id is ACSD-4769. De kwestie is al opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er is een interne serverfout bij het importeren van producten met aanpasbare opties.

<u> Stappen om </u> te reproduceren:

1. Maak een extra winkelweergave. Zorg ervoor dat u 2 winkelweergaven hebt, bijvoorbeeld en, VK.
1. Maak twee eenvoudige producten, bijvoorbeeld prod1 en prod2.
1. Bereid een csv- dossier voor dat douaneopties voor beide producten in elke opslagmening en voor het **Al werkingsgebied van de Mening van de Opslag** toevoegt. Importeer dit CSV-bestand.
1. Maak een ander CSV-bestand dat twee records bevat. Het eerste verslag zou moeten zijn om de douaneopties van &quot;prod1&quot;specifiek voor het gebied van de de opslagmening van het VK bij te werken en het tweede verslag zou de douaneopties van &quot;prod2&quot;voor het **Al werkingsgebied van de Mening van de Opslag moeten zijn**. Importeer dit tweede CSV-bestand.

<u> Verwachte resultaten </u>:

U moet opties zonder fouten kunnen aanpassen.

<u> Ware resultaten </u>:

Er treedt een schending van een integriteitsbeperking op.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
