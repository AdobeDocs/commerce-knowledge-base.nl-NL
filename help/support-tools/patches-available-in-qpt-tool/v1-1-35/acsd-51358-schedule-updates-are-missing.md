---
title: 'ACSD-51358: planningupdates ontbreken'
description: Pas de ACSD-51358-patch toe om het Adobe Commerce-probleem op te lossen waarbij de wijzigingen in de geplande update zonder einddatum ertoe leiden dat andere geplande updates op dezelfde entiteit worden verwijderd.
feature: Staging
role: Admin, Developer
exl-id: 8bc4c505-9cf2-4c33-93a1-4b4d7d0dfc15
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51358: planningupdates ontbreken

De ACSD-51358-patch verhelpt het probleem waarbij de wijzigingen in de geplande update zonder einddatum ertoe leiden dat andere geplande updates voor dezelfde entiteit worden verwijderd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 is geïnstalleerd. De patch-id is ACSD-51358. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De wijzigingen in de geplande update zonder einddatum leiden tot het verwijderen van andere geplande updates voor dezelfde entiteit.

<u>Stappen om te reproduceren</u>:

1. Een **[!UICONTROL scheduled update]** zonder de einddatum (*update 1*).
1. Nieuw maken **[!UICONTROL scheduled update]** met dezelfde begindatum als de eerste update, maar voeg de volgende dag en de einddatum toe (*update 2*).
1. Bewerken **[!UICONTROL scheduled update]** gemaakt op stap 1 (*update 1*) en de wijzigingen opslaan.

<u>Verwachte resultaten</u>

The (*update 2*) moet in de **[!UICONTROL schedule update]** list when (*update 1*) wordt bewerkt.

<u>Werkelijke resultaten</u>

The (*update 2*) is verwijderd uit de **[!UICONTROL schedule update]** list when (*update 1*) wordt bewerkt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
