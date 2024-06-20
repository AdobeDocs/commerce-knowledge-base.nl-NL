---
title: "ACSD-52041: Bij het renderen van Page Builder worden geen vergrendelingen vrijgegeven."
description: Pas de ACSD-52041-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de Page Builder vijf seconden lang wordt weergegeven zonder vergrendelingen vrij te geven.
feature: Page Builder
role: Admin, Developer
exl-id: f2a1fd36-2098-46a7-aa42-3a5a0014adc9
source-git-commit: fc5dc9fcf610cae6f8c0a334b4ef15029c462c66
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-52041: Bij het renderen van Page Builder worden geen vergrendelingen vrijgegeven

De ACSD-52041-patch verhelpt het probleem waarbij de Page Builder vijf seconden lang rendert zonder vergrendelingen vrij te geven. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.48 is geïnstalleerd. De patch-id is ACSD-52041-v2. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p8, 2.4.5 - 2.4.5-p7, 2.4.6 - 2.4.6-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De Page Builder wordt gedurende vijf seconden weergegeven zonder vergrendelingen vrij te geven.

<u>Stappen om te reproduceren</u>:

1. Bewerk een CMS-pagina, productpagina of iets anders met Page Builder.
1. Sla de wijzigingen op.
1. Let op de pagina die tijd bespaart.

<u>Verwachte resultaten</u>

De inhoud wordt opgeslagen. Geen fouten gevonden in browserlogboek.

<u>Werkelijke resultaten</u>

De besparing duurt langer dan de gebruikelijke tijd om te voltooien.
Fout in console: ``Page Builder was rendering for 5 seconds without releasing locks``

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
