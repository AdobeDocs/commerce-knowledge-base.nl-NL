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

De ACSD-47669-patch verhelpt het probleem waarbij een interne serverfout optreedt tijdens het importeren van producten met aanpasbare opties. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.38 is geïnstalleerd. De patch-id is ACSD-4769. De kwestie is al opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er is een interne serverfout bij het importeren van producten met aanpasbare opties.

<u>Stappen om te reproduceren</u>:

1. Maak een extra winkelweergave. Zorg ervoor dat u 2 winkelweergaven hebt, bijvoorbeeld en, VK.
1. Maak twee eenvoudige producten, bijvoorbeeld prod1 en prod2.
1. Een CSV-bestand voorbereiden waarin aangepaste opties voor beide producten in elke winkelweergave en voor de **Alle winkelweergave** bereik. Importeer dit CSV-bestand.
1. Maak een ander CSV-bestand dat twee records bevat. De eerste record zou moeten bestaan uit het bijwerken van de aangepaste opties van &#39;prod1&#39;, specifiek voor het weergavebereik van de Britse winkel, en de tweede record zou moeten bestaan uit het bijwerken van de aangepaste opties van &#39;prod2&#39; voor de **Alle winkelweergave** bereik. Importeer dit tweede CSV-bestand.

<u>Verwachte resultaten</u>:

U moet opties zonder fouten kunnen aanpassen.

<u>Werkelijke resultaten</u>:

Er treedt een schending van een integriteitsbeperking op.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
